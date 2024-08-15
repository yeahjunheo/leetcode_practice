# twoSum

## Prompt

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

Example 1:
> Input: nums = [2, 7, 11, 15], target = 9\
> Output: [0, 1]\
> Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Example 2:
> Input: nums = [3, 2, 4], target = 6\
> Output: [1, 2]

Example 3:
> Input: nums = [3, 3], target = 6\
> Output: [0, 1]

## Brainstorm

We know that we need to find a pair of integers AND they will sum up to the `target`. 

One solution would be to take one integer, subtract it from the `target`, then see if the remainder exists in `num`. This way, we can check once. This works since we know there is one solution for each `num` and we don't need to sort since sorting will just take up more time. 

```pseudo
iterate over num
    subtract the value from target
    check if remainder exists in num
    if yes 
        return the pair
return false \\since a solutino exists, we don't need this but its a fail-safe
```

## Solution
```go
func twoSum(nums []int, target int) []int {
    for i := 0; i < len(nums); i++ {
        num1 := nums[i]
        num2 := target - num1
        if j := indexOf(nums[i+1:], num2); j != -1 {
            return []int{i, i+j+1}
        }
    }
    return []int{0, 0}
}

func indexOf(nums []int, target int) int {
    for i, b := range nums {
        if b == target {
            return i
        }
    }
    return -1
}
```