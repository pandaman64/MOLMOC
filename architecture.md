# CPU Architecture
- stack machine
- 1 word = 8 bit
- instruction length = 1 word
- variable CPI(clocks per instruction)
  - stack operation -> 1 clock
  - immediate operation -> 2 clocks

# Instructions
## Overview
| immediate flag(1bit) | opcode(7bit) or length(2bit) + opcode(5bit) |

### Stack Operations
| 0 | opcode(7bit) |

|bit code  |operation|description|
|----------|--------:|-----------|
|0 000 0000|      NOP|no operation|
|0 000 0001|      ADD|x y -> x + y|
|0 000 0010|      SUB|x y -> x - y|
|0 000 0011|      AND|x y -> x & y|
|0 000 0100|       OR|x y -> x | y|
|0 000 0101|       SL|x -> x << 1|
|0 000 0110|       SR|x -> x >> 1|
|0 000 1000|      POP|x ->|
|0 000 1001|      DUP|x -> x x|
|0 001 0000|     JMPS|x ->; pc <= x|
|x xxx xxxx|and more...|

### Immediate Operations
| 1 | length(2bit) | opcode(5bit) |

Words following the instruction represent the operand, arranged in the little-endian.
The length of the immediate value is determined by the *length* field.

|bit code  |operation|description|
|----------|--------:|-----------|
|1 xx 00000|     LOAD| -> imm |
|1 xx 00001|     POPX|x_1 x_2 .. x_imm -> |
|1 xx 10000|     JMPI|pc <= imm |
|1 xx 11111|     CALL|pc <= imm; cs <= pc + 1 |
|x xx xxxxx|anything else?|
