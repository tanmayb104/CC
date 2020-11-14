## Dynamic Programming

### [Count Sorted Vowel Strings](https://leetcode.com/problems/count-sorted-vowel-strings/)

```python
class Solution:
    def countVowelStrings(self, n: int) -> int:
        dp=[[0 for i in range(n)] for j in range(6)]
        for i in range(1,6):
            dp[i][0]=1
        for i in range(1,n):
            for j in range(1,6):
                dp[j][i]=dp[j][i-1]+dp[j-1][i]
        c=0
        for i in range(1,6):
            c+=dp[i][n-1]
        print(dp)
        return (c)  
```


### [Divisor Game](https://leetcode.com/problems/divisor-game/)

```python
class Solution:
    def divisorGame(self, N: int) -> bool:
        dp=[0 for i in range(N+1)]
        for i in range(1,N+1):
            for j in range(1,i):
                if(i%j==0):
                    dp[i]=max(dp[i],not dp[i-j])
        if(dp[N]):
            return True
        else:
            return False
```


### [House Robber](https://leetcode.com/problems/house-robber/)

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        if(len(nums)>1):
            nums[1]=max(nums[1],nums[0])
        for i in range(2,len(nums)):
            nums[i]=max(nums[i-1],nums[i]+nums[i-2])
        if(len(nums)):
            return nums[-1]
        else:
            return 0
```
