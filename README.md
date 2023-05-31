# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
1.Create a new project in QuartusII software.

2.Name the project as uc for upcounter and dc for down counter.

3.Create a new verilog hdl file in the project file.

4.Name the module as dc and uc for down counter and up counter.

5.Within the module declare input and output variables.

6.Create a loop using if-else with condition parameter as reset value.

7.End the loop.

8.End the module.
### PROGRAM 
```python
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by:Shaik Sameer Basha 
RegisterNumber:  212222240093
# Up Counter
module uc(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
A[3]=(((A[2]) & (A[1]) & (A[0]))^A[3]);
A[2]=(((A[1]) & (A[0]))^A[2]);
A[1]=((A[0])^A[1]);
A[0]=1^A[0];
end
endmodule
# DownCounter
module dc(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
A[3]=(((~A[2]) & (~A[1]) & (~A[0]))^A[3]);
A[2]=(((~A[1]) & (~A[0]))^A[2]);
A[1]=((~A[0])^A[1]);
A[0]=1^A[0];
end
endmodule
```
### RTL LOGIC UP COUNTER AND DOWN COUNTER  
#### UP COUNTER
![uc rtl](https://github.com/shaikSameerbasha5404/Exp-7-Synchornous-counters-/assets/118707756/cbbf816c-8b83-4c55-9e15-bedb41350ae5)
#### Down COUNTER
![dc rtl](https://github.com/shaikSameerbasha5404/Exp-7-Synchornous-counters-/assets/118707756/3a5f57b3-363f-4c05-b39d-d1951741fddf)
### TIMING DIGRAMS FOR COUNTER  
![Screenshot (128)](https://github.com/shaikSameerbasha5404/Exp-7-Synchornous-counters-/assets/118707756/86af9c77-6318-420c-9f6d-978d7f7c5e3f)

![Screenshot (130)](https://github.com/shaikSameerbasha5404/Exp-7-Synchornous-counters-/assets/118707756/9ef3d0d8-56f0-44ed-ae47-65c7aece0a2d)

### TRUTH TABLE 
![198290799-2e8450bf-df1c-4588-94bc-2a19f756ee28](https://github.com/shaikSameerbasha5404/Exp-7-Synchornous-counters-/assets/118707756/e0235645-29a9-4ef4-b98f-0114e54cea45)


![198290826-8317087f-c170-4c0a-83ac-7d0ac1a6c162](https://github.com/shaikSameerbasha5404/Exp-7-Synchornous-counters-/assets/118707756/cf061e89-4b80-48f0-b8ed-6035f07bd1ae)


### RESULTS 
The 4 bit up and down counters has been implemented and validated the functionality.
