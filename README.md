# VLSI-LAB-EXPERIMENTS

EXPERIMENT - 1:


AIM:

    To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED:


    Xilinx 14.7 Spartan6 FPGA

PROCEDURE:

STEP:1 Start the Xilinx navigator, Select and Name the New project.


STEP:2 Select the device family, device, package and speed.


STEP:3 Select new source in the New Project and select Verilog Module as the Source type.


STEP:4 Type the File Name and Click Next and then finish button. Type the code and save
it.


STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.


STEP:6 Click the simulation to simulate the program and give the inputs and verify the
outputs as per the truth table.


STEP:7 Select the Implementation in the Sources Window and select the required file in
the Processes Window.


STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan
Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User
constraint File) is obtained.


STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc
column Select save from the File menu.


STEP:10 Double click on the Implement Design and double click on the Generate
Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.


STEP:11 Load the Bit file into the SPARTAN 6 FPGA



STEP:12 On the board, by giving required input, the LEDs starts to glow light, indicating
the output.



Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


VERILOG CODE:


```

module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule

````

output:

![Screenshot 2024-02-17 143536](https://github.com/porkodivasu/VLSI-LAB-EXP-1/assets/160757120/6f6de73b-baa6-4ebe-a420-d72cea1224e5)

Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

VERILOG CODE:

```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
and g1(carry,a,b);
xor g2(sum,a,b);
endmodule
```

OUTPUT:

Half Adder:

![Screenshot (85)](https://github.com/porkodivasu/VLSI-LAB-EXP-1/assets/160757120/88106e47-e9f7-42da-93d4-0390ee24eaa4)

Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

VERILOG CODE:

```

module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
xor g2(sum,w1,c);
and g3(w2,w1,c);
and g4(w3,a,b);
or g5(carry,w2,w3);
endmodule

```

OUTPUT:

![Screenshot (16)](https://github.com/porkodivasu/VLSI-LAB-EXP-1/assets/160757120/18f954a4-39a2-4a4e-bf2c-696bca3fe37c)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

VERILOG CODE:


```

module halfsubtractor(a,b,difference,borrow);
input a,b;
output difference,borrow;
xor (difference,a,b);
and (borrow,~a,b);
endmodule

```
output:

![Screenshot (16)](https://github.com/porkodivasu/VLSI-LAB-EXP-1/assets/160757120/aaac5104-7808-40dc-9c78-497ac3bc82a8)


Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

VERILOG CODE:


```

module fullsubtractor (a,b,c,difference,borrow);
input a,b,c;
output difference,borrow;
wire w1,w2,w3;
xor g1(w1,a,b);
xor g2(difference,w1,c);
and g3(w2,~a,b);
and g4(w3,w1,c);
or g5(borrow,w3,w2);
endmodule
```

OUTPUT:


![Screenshot (17)](https://github.com/porkodivasu/VLSI-LAB-EXP-1/assets/160757120/5805f079-c47b-4be8-b3ab-14853a679caa)


8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

VERILOG CODE:

```

module fa(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum=a^b^c;
assign carry=(a&b)|(b&c)|(c&a);
endmodule

module rca(a,b,cin,sum,cout);
input [7:0]a,b;
input cin;
output [7:0]sum;
output cout;
wire [7:1]w;
fa f1(a[0],b[0],cin,sum[0],w[1]);
fa f2(a[1],b[1],w[1],sum[1],w[2]);
fa f3(a[2],b[2],w[2],sum[2],w[3]);
fa f4(a[3],b[3],w[3],sum[3],w[4]);
fa f5(a[4],b[4],w[4],sum[4],w[5]);
fa f6(a[5],b[5],w[5],sum[5],w[6]);
fa f7(a[6],b[6],w[6],sum[6],w[7]);
fa f8(a[7],b[7],w[7],sum[7],cout);
endmodule
```

output:

![Screenshot (20)](https://github.com/porkodivasu/VLSI-LAB-EXP-1/assets/160757120/1332fb3b-130c-410f-ae99-d280dfade3f4)

RESULT:

Thus the simulation and synthesis of Logic Gates,Adders and Subtractors using
vivado has been sucessfully executed and verified.

