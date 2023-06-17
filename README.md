# Motor Position Correction

## Problem
As part of my research work at the [CBA lab](https://cba.mit.edu/), I assisted [Jake Read](https://jakeread.pages.cba.mit.edu/) in his work to develop better fabrication machines.

To achieve that, we built a motor driver that allows us to use any stepper motor as a servo motor by writing the motor a target position, and not a desired amount of steps to move.
The system consists of a motor and an encoder, that measures the motor position at any given time. The position values are integers from `0-16383` that represent the angle of which the motor is facing.<br>

Unfortunately, the encoder and the motor shaft are slightly misaligned, resulting in deviated readings of the encoder.

<br>

## Solution
This algorithm fix this issue by comparing the encoder readings to a perfect sawtooth, fitting a function to this deviation, and creating a lookup table for the motor firmware such that a target position can be translated into the actual motor shaft angle, and not the misaligned encoder value.

The was tested on a real system and produced a smooth and consistent motion.<br>
The effect was noticeable enough and it was possible to hear the difference between the 'wabbly' motion without the algorithm and the clean movement with it. 
