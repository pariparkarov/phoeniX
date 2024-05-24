Computer Organization - Spring 2024
==============================================================
## Iran Univeristy of Science and Technology
## Assignment 1: Assembly code execution on phoeniX RISC-V core

- Name:Parsa Amiri
- Team Members:Mohamad Amin Mirzaabassi, Rasa Ghorban Alizadeh
- Student ID: 400411153
- Date:5/23/2024

## Report

**integer_square_root**:

The code use the binary search alghorithm to find the square root. The number is loaded into register a0 and with the binary_search loop, the square of the number less than equal of the number loaded into a0 is found.
The code enters a loop labeled `binary_search` which performs the binary search algorithm: It checks if the low bound (`t0`) is greater than the high bound (`t1`). If so, it exits the loop. It calculates the mid value as `(low + high) / 2` and stores it in `t2`. It calculates `mid * mid` and stores the result in `t3`. It compares `t3` (mid squared) with the input number (`a0`):
    - If `t3 < a0`, it means the square root is greater than `mid`, so it updates the low bound to `mid + 1` and jumps back to `binary_search`.
    - If `t3 > a0`, it means the square root is less than `mid`, so it updates the high bound to `mid - 1` and jumps back to `binary_search`.
    - If `t3 == a0`, it means `mid` is the square root, so it stores `mid` in `t1` (result register) and exits the loop.
![alt text](image.png)
The output is t2.

**quick_sort**:
The last number of the array is used as pivot.

 main function
- Initializes the stack pointer and allocates space for local variables.
- Initializes an array `arr` with the values `[6, 6, 1, 2, 4]`.
- Sets up arguments for the `quicksort` function call:
- `a0` holds the base address of the array.
- `a1` holds the low index (0).
- `a2` holds the high index (4).
- Calls the `quicksort` function.
- After the sorting is done, it loads the sorted elements back into registers `s2` through `s6` for inspection.
- Restores registers and deallocates the stack space before exiting.

quicksort function
- Implements the recursive QuickSort algorithm.
- Saves registers and arguments on the stack.
- Checks the base case: If `low >= high`, it returns without doing anything.
- Calls the `partition` function to partition the array around a pivot element, receiving the pivot index in `a0`.
- Recursively calls itself for the left and right partitions of the array.
- Restores registers and arguments from the stack before returning.

partition function
- Implements the partition step of the QuickSort algorithm.
- Saves registers on the stack.
- Selects the last element (`array[high]`) as the pivot element.
- Initializes two indices `i` and `j`.
- Iterates through the array:
- If `array[j] <= pivot`, it swaps `array[i+1]` and `array[j]` and increments `i`.
- Increments `j` in any case.
- After the loop, it swaps the pivot element with `array[i+1]`.
- Returns the final value of `i` (the pivot index) in `a0`.
- Restores registers from the stack before returning.
![alt text](image.png)
The outputs are s2 and s6.
