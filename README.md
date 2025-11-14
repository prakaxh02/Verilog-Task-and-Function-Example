# **EXP4: 4-bit Ripple Carry Adder using Task and 4-bit Ripple Counter using Function with Testbench**

---

## **Aim**
To design, simulate, and verify a **4-bit Ripple Carry Adder** using **Task** and a **4-bit Ripple Counter** using **Function** in Verilog HDL.

---

## **Apparatus Required**
- System with **Vivado Design Suite**
---

## **Theory**
### **Ripple Carry Adder**
A 4-bit Ripple Carry Adder (RCA) adds two 4-bit binary numbers by cascading four full adders. The carry-out of each full adder acts as the carry-in for the next stage. Using a **task** in Verilog, the addition operation can be modularized for each bit.
<img width="692" height="268" alt="image" src="https://github.com/user-attachments/assets/b70c348a-049a-4462-88a4-ad6905446cf4" />


### **Ripple Counter**
A Ripple Counter is a sequential circuit that counts in binary. In a 4-bit ripple counter, the output of one flip-flop serves as the clock input for the next flip-flop. Using a **function** in Verilog allows the counting logic to be encapsulated and reused.

<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/fa8730fc-e48e-477a-b2e3-6697a95355d3" />

---

## **Program**

### **4-bit Ripple Carry Adder using Task**

```verilog
// 4-bit Ripple Carry Adder using Task
module ripple_carry_adder_task(
    input [3:0] A, B,
    output [3:0] SUM,
    output COUT
);
    reg [3:0] sum_temp;
    reg cout_temp;

    task full_adder;
        input a, b, cin;
        output s, cout;
        begin
            s = a ^ b ^ cin;
            cout = (a & b) | (b & cin) | (a & cin);
        end
    endtask






Type the Program



endmodule
```

### **Test bench 4-bit Ripple Carry Adder using Task**
```
module tb_ripple_carry_adder_task;
    reg [3:0] A, B;
    wire [3:0] SUM;
    wire COUT;

    ripple_carry_adder_task uut (A, B, SUM, COUT);

    initial begin




        $finish;
    end
endmodule
```
### 4-bit Ripple Carry Adder Simulation Output 

<img width="1253" height="645" alt="image" src="https://github.com/user-attachments/assets/340a31d8-a63e-4af6-809d-ae3c518039f3" />





### **4-bit Ripple Counter using Function**
```
// 4-bit Ripple Counter using Function
module ripple_counter_func(
    input clk, reset,
    output reg [3:0] count
);
    function [3:0] increment;
        input [3:0] val;
        begin
            increment = val + 1;
        end
    endfunction





endmodule
```
### **Testbench for 4-bit Ripple Counter using Function**
```
module tb_ripple_counter_func;
    reg clk, reset;
    wire [3:0] count;

    ripple_counter_func uut (clk, reset, count);

    initial begin
        clk = 0;
        forever #5 clk = ~clk; // Clock with 10ns period
    end

    initial begin
     
    end
endmodule
```
### 4-bit Ripple Counter Simulation output 
<img width="1917" height="1141" alt="image" src="https://github.com/user-attachments/assets/80d7121d-b9bc-43c1-8886-11c5b1fe5196" />






### Result

The simulation of the 4-bit Ripple Carry Adder using Task and 4-bit Ripple Counter using Function was successfully carried out in Vivado Design Suite.
Both designs produced correct functional outputs as verified by waveform and console output.
