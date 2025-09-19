# Flipflop-using-Blocking-and-Non-blocking-Assignments
Exp 3 -Write and simulate D, SR, JK, T Flipflops using Blocking and Non blocking Assignments
   Aim: To design and simulate D, SR, JK, T Flipflops using Blocking and Non blocking Assignments in Verilog HDL and verify its functionality through a testbench using the Vivado 2023.1 simulation environment.
   
  Apparatus Required:
  Vivado 2023.1
Procedure:

Launch Vivado Open Vivado 2023.1 by double-clicking the Vivado icon or searching for it in the Start menu. 
Create a New Project Click on "Create Project" from the Vivado Quick Start window. In the New Project Wizard: Project Name: Enter a name for the project (e.g., Mux4_to_1). 
Project Location: Select the folder where the project will be saved. Click Next. 
Project Type: Select RTL Project, then click Next. Add Sources: Click on "Add Files" to add the Verilog files (e.g., mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.). 
Make sure to check the box "Copy sources into project" to avoid any external file dependencies. 
Click Next.
Add Constraints: Skip this step by clicking Next (since no constraints are needed for simulation). 
Default Part Selection: You can choose a part based on the FPGA board you are using (if any). 
If no board is used, you can choose any part, for example, xc7a35ticsg324-1L (Artix-7). 
Click Next, then Finish.
Add Verilog Source Files In the "Sources" window, right-click on "Design Sources" and select Add Sources if you didn't add all files earlier.
Add the Verilog files and the testbench. 
Check Syntax Expand the "Flow Navigator" on the left side of the Vivado interface. 
Simulate the Design In the Flow Navigator, under "Simulation", click on "Run Simulation" → "Run Behavioral Simulation". 
Vivado will open the Simulations Window, and the waveform window will show the signals defined in the testbench. 
View and Analyze Simulation Results Adjust Simulation Time To run a longer simulation or adjust timing, go to the Simulation Settings by clicking "Simulation" → "Simulation Settings". Under "Simulation", modify the Run Time (e.g., set to 1000ns).
Generate Simulation Report Once the simulation is complete, you can generate a simulation report by right-clicking on the simulation results window and selecting "Export Simulation Results".
Save the report for reference in your lab records. Save and Document Results Save your project by clicking File → Save Project.
Take screenshots of the waveform window and include them in your lab report to document your results. 
You can include the timing diagram from the simulation window showing the correct functionality of the Seven Segment across different select inputs and data inputs. 
Close the Simulation Once done, by going to Simulation → "Close Simulation

Input/Output Signal Diagram:


RTL Code:
```
module sr_ff (
    input wire S, R, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
```
module jk_ff (
    input wire J, K, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
```
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```

TestBench:
```
module sr_ff_tb;
reg clk, S, R;
wire Q;
sr_ff uut (.clk(clk),.S(S),.R(R),.Q(Q));
initial begin
clk = 0;
forever #10 clk = ~clk;
end
initial begin
S = 0; R = 0;
#100 S = 1; R = 0;
#100 S = 0; R = 0;
#100 S = 0; R = 1;
#100 S = 1; R = 1;
#100 S = 0; R = 0;
end

```
```
module tb_jk_ff;
reg clk;
reg J, K;
wire Q;
jk_ff uut (.clk(clk),.J(J),.K(K),.Q(Q));
initial begin
clk=0;
forever #20 clk=~clk;
end
initial begin
J = 0; K = 0;
#100 J=0; K=0;
#100 J=0; K=1;
#100 J=1; K=0;
#100 J=1; K=1;
#100 J=0; K=1;
#100 J=1; K=0;
#100 J=1; K=1;
end
endmodule
```
```
module t_ff_tb;
reg clk, rst, T;
wire Tout;
t_ff uut (.clk(clk),.rst(rst),.T(T),.Tout(Tout));
initial begin
clk = 0;
forever #10 clk = ~clk;
end
initial begin
rst = 1; T = 0;
#20 rst = 0;
#20 T = 1;
#20 T = 0;
#20 T = 1;
#20 T = 1;
#20 T = 0;
end
endmodule
```
```
module dff_tb;
reg clk_t, rst_t, d_t;
wire q_t;
dff dut (.clk(clk_t),.rst(rst_t),.d(d_t),.q(q_t) );
initial begin
clk_t = 1'b0;
rst_t = 1'b1;
d_t = 1'b0;
#100 rst_t = 1'b0;
#100 d_t = 1'b1;
#100 d_t = 1'b0;
#100 d_t = 1'b1;
end
always #10 clk_t = ~clk_t;
endmodule
```
Output waveform:
![WhatsApp Image 2025-09-17 at 20 18 35_7ce85bdc](https://github.com/user-attachments/assets/8b80e4dc-d5f0-4559-9909-e87482dc69e1)
![WhatsApp Image 2025-09-17 at 20 18 36_ff9eeb43](https://github.com/user-attachments/assets/cddf19a0-3574-4015-8b3f-ac531ecd767c)
![WhatsApp Image 2025-09-17 at 20 18 36_d90022e5](https://github.com/user-attachments/assets/cab46979-d38f-4545-a621-8c256fbfb8ae)
![WhatsApp Image 2025-09-17 at 20 18 36_871d41e0](https://github.com/user-attachments/assets/938ebba2-3b45-44df-905c-a3d01d68a750)

Conclusion:

All flip-flops (SR, D, JK, T) were successfully simulated using blocking statements in Verilog HDL. The outputs matched the expected truth table values, demonstrating correct sequential behavior.
