#Week 9 Whiteboarding Problems

##Easy:

###1:  Move 0's
####Problem Description
Given an array nums, write a function to move all 0's to the end of it while maintaining 
the relative order of the non-zero elements. For example, given nums = [0, 1, 0, 3, 12], 
after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.


@param {number[]} nums
@return {void}




####A solution:
```
var moveZeroes = function(nums) {
	var count = 0;
	var i = 0;
	while(i < nums.length - count) {
		if(nums[i] === 0) {
			nums.push(nums.splice(i,1)[0]);
			count++;
		} else {
			i++;
		}
	}
};
```

###2:  Number of 1-Bits
####Problem Description
Write a function that takes an unsigned integer and returns the number 
of ’1' bits it has (also known as the Hamming weight).
For example, the 32-bit integer ’11' has binary representation 
00000000000000000000000000001011, so the function should return 3.


@param {number} n - a positive integer
@return {number}



####A Solution

```
var hammingWeight = function(n) {
	// creating variable and converting n to a string of binary
	var count = 0;
	n = n.toString(2);
	n = n.split('');
	// looping through n to find 1-bits
	for(var i = 0; i < n.length; i++){
		if(n[i] === '1') {
			count++;
		}
	}
	return count;
};
```

##Hard
###3 Perfect Squares

####Problem Description
Given two whole numbers, A and B, write a function that returns the number of perfect squares (a number that has a whole square root) between A and B. You can assume that A is less than or equal to B.

####Example

Given A = 2 and B = 17, the perfect squares between A and B are 4, 9, and 16 so the function should return `3`


###4 Pascal's Triangle Matrix

####Problem Description 
Create a function, pascals(n) that prints Pascal's Triangle inside of a Matrix that is n layers high.

####Example

```
pascals(4) = [
							[1],
							[1, 1],
							[1, 2, 1],
							[1, 3, 3, 1]
						 ]	
```

####a solution

```
var generate = function(n) {
  if(n <= 0) {
    return [];
  } else if(n == 1) {
    return [[1]];
  } else {
    var tri = [[1],[1,1]];
    while(tri.length < n) {
      tri.push([1]);
      for(var i = 0; i < tri.length-1; i++) {
        tri[tri.length - 1].push(tri[tri.length - 2][i - 1] + tri[tri.length - 2][i]);
      }
      tri[tri.length - 1].push(1);
    }
    return tri;
  }
};
```
