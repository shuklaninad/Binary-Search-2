# Binary-Search-2
Explain your approach in **three sentences only** at top of your code


## Problem 1: (https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if nums == None or len(nums) == 0:
            return [-1, -1]
        
        first = self.binarySearchFirst(nums, target)
        if first == -1:
            return [-1, -1]
        second = self.binarySearchSecond(nums, target)
        return [first, second]
    
    def binarySearchFirst(self, nums: List[int], target: int) -> int:
        low = 0
        high = len(nums) - 1
        while low <= high:
            mid = low + (high - low) // 2
            if nums[mid] == target:
                if mid == 0 or nums[mid - 1] < nums[mid]:
                    return mid
                else:
                    high = mid - 1
            elif target > nums[mid]:
                low = mid + 1
            else:
                high = mid - 1
        return -1
    
    def binarySearchSecond(self, nums: List[int], target: int) -> int:
        low = 0
        high = len(nums) - 1
        while low <= high:
            mid = low + (high - low) // 2
            if nums[mid] == target:
                if mid == len(nums) - 1 or nums[mid + 1] > nums[mid]:
                    return mid
                else: 
                    low = mid + 1
            elif target > nums[mid]:
                low = mid + 1
            else: high = mid - 1
        return -1 

## Problem 2: (https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

class Solution:
    def findMin(self, nums: List[int]) -> int:
        if nums == None or len(nums) == 0:
            return -1
        
        low = 0
        high = len(nums)-1

        while low <= high:
            if nums[low] <= nums[high]:
                return nums[low]
            mid = low + (high - low) // 2
            if (mid == 0 or nums[mid] < nums[mid-1]) and (mid == len(nums)-1 or nums[mid] < nums[mid+1]):
                return nums[mid]
            if nums[low] <= nums[mid]:
                low = mid + 1
            else:
                high = mid - 1

        return 22 ## we will never hit this value. There will always be a minimum value.



## Problem 3: (https://leetcode.com/problems/find-peak-element/)

class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        low = 0
        high = len(nums) - 1
        while low <= high:
            mid = low + (high - low) // 2
            if(mid == 0 or nums[mid - 1] < nums[mid]) and (mid == len(nums)-1 or nums[mid + 1] < nums[mid]):
                return mid
            elif mid != 0 and nums[mid-1] > nums[mid]:
                high = mid - 1
            else:
                low = mid + 1
        return 22 #we will never reach here as there will always be a peak number

