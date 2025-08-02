<!---
![Digital_VLSI_SoC_Design_ _Planning_(RTL2GDSII_Flow)1](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/92eb860b-7a88-4c6f-8143-ad3e09fd9c5b)
![Digital_VLSI_SoC_Design_ _Planning_(RTL2GDSII_Flow) (1)1](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/4285c5e4-d5df-43e4-b460-ead45ff67f9b)
-->

# Digital VLSI SoC Design and Planning


> 2 Week digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD in collaboration with NASSCOM

## Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK (16/07/2025 - 17/07/2025)

### Theory

#### Package

* In any embedded board we have seen, the part of the board we consider as the chip is only the ***PACKAGE*** of the chip which is nothing but a protective layer or packet bound over the actual chip and the actual manufatured chip is usually present at the center of a package wherein, the connections from package is fed to the chip by ***WIRE BOUND*** method which is none other than basic wired connection.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7562205a-7435-46c7-a66e-de1626911f14)
![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7005a9e3-79da-4590-bea0-eb3768127a3d)
![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/70b1c678-2a2e-484f-9181-812dbcd5f0a3)

#### Chip

* Now, taking a look inside the chip, all the signals from the external world to the chip and vice versa is passed through ***PADS***. The area bound by the pads is ***CORE*** where all the digital logic of the chip is placed. Both the core and pads make up the ***DIE*** which is the basic manufacturing unit in regards to semiconductor chips.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d65a0ddf-2f86-4bbc-8d36-b02e09a1483e)

* ***FOUNDRY*** is the place where the semiconductor chips are manufactured and ***FOUNDRY IP's*** are Intellectual Properties based on a specific foundry and these IP's require a specific level of intelligence to be produced whereas, repeatable digital logic blocks are called ***MACROS***.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ed1cd25e-6270-4b84-8f0d-f0ea7c8a7ef8)

#### ISA (Intruction Set Architecture)

* A C program which has to be run on a specific hardware layout which is the interior of a chip in your laptop, there is certain flow to be followed.
* Initially, this particular C program is compiled in it's assembly language program which is nothing but ***RISC-V ISA (Reduced Instruction Set Compting - V Intruction Set Architecture)***.
* Following this, the assembly language program is then converted to machine language program which is the binary language logic 0 and 1 which is understood by the hardware of the computer.
* Directly after this, we've to implement this RISC-V specification using some ***RTL (a Hardware Description Language)***. Finally, from the RTL to ***Layout*** it is a standard PnR or RTL to GDSII flow.

![Screenshot (278)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7dc4601a-e386-48e5-9d1f-7fa5b47ca0ba)

* For an application software to be run on a hardware there are several processes taking place. To begin with, the apps enters into a block called system software and it converts the application program to binary language. There are various layers in system software in which the major layers or components are OS (Operating System), Compiler and Assembler.
* At first the OS outputs are small function in C, C++, VB or Java language which are taken by the respective compiler and converted into instructions and the syntax of these instructions varies with the hardware architecture on which the system is implemented.
* Then, the job of the assembler is to take these instructions and convert it into it's binary format which is basically called as a machine language program. Finally, this binary language is fed to the hardware and it understands the specific functions it has to perform based on the binary code it receives.

![Screenshot (279)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/19e8b634-f209-41a6-928d-6fba66f5b177)

* For example, if we take a stopwatch app on RISC-V core, then the output of the OS could be a small C function which enters into the compiler and we get output RISC-V instructions following this, the output of the assembler will be the binary code which enters into your chip layout.

![Screenshot (280)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7d4570ca-82a6-4abe-81d2-067ebb9b2c15)

* For the above stopwatch the following are the input and output of the compiler and assembler.

![Screenshot (281)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/d7b7fd1b-21ee-46b7-9a91-8314bd753a51)

* The output of the compiler are instructions and the output of the assembler is the binary pattern. Now, we need some RTL (a Hardware Description Language) which understands and implements the particular instructions. Then, this RTL is synthesised into a netlist in form of gates which is fabricated into the chip through a physical design implementation.

![Screenshot (282)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/e349cb06-45e3-4ae4-b85f-9020a0a62737)

* There are mainly 3 different parts in this course. They are:
1. RISC-V ISA
2. RTL and synthesis of RISC-V based CPU core - picorv32
3. Physical design implementation of picorv32

![Screenshot (283)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/832f0ea6-2d60-4d9a-937c-a2dedd5f8cac)

#### Open-source Implementation

* For open-source ASIC design implemantation, we require the following enablers to be readily available as open-source versions. They are:-
1. RTL Designs
2. EDA Tools
3. PDK Data

* Initially in the early ages, the design and fabrication of IC's were tightly coupled and were only practiced by very few companies like TI, Intel, etc.
* In 1979, Lynn Conway and Carver Mead came up with an idea to saperate the design from the fabrication and to do this they inroduced structured design methodologies based on the λ-based design rules and published the first VLSI book "Introduction to VLSI System" which started the VLSI education.
* This methodology resulted in the emergence of the design only companies or ***"Fabless Companies"*** and fabrication only companies that we usually refer to as ***"Pure Play Fabs"***.
* The inteface between the designers and the fab by now became a set of data files and documents, that are reffered to as the ***"Process Design Kits (PDKs)"***.
* The PDK include but not limited to Device Models, Technology Information, Design Rules, Digital Standard Cell Libraries, I/O Libraries and many more.
* Since, the PDK contained variety of informations, and so they were distributed only under NDAs (Non-Disclosure Agreements) which made it in-accessible to the public.
* Recently, Google worked out an agreement with skywater to open-source the PDK for the 130nm process by skywater Technology, as a result on 30 June 2020 Google released the first ever open-source PDK.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/87384374-e66b-4ec6-b9c4-3fb92ad4d275)

* ASIC design is a complex step that involves tons of steps, various methodologies and respective EDA tools which are all required for successful ASIC implementation which is achieved though an ASIC flow which is nothing but a piece of software that pulls different tools togather to carry out the design process.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/1762d6d6-c5f8-4bd9-8a3d-968eb4360889)

#### OpenLANE Open-source ASIC Design Implementation Flow

* The main objective of the ASIC Design Flow is to take the design from the RTL (Register Transfer Level) all the way to the GDSII, which is the format used for the final fabrication layout.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/533f58ee-4524-4a18-abb5-36b4d6a56b1f)

* Synthesis is the process of convertion or translation of design RTL into circuits made out of Standard Cell Libraries (SCL) the resultant circuit is described in HDL and is usually reffered to as the Gate-Level Netlist.
* Gate-Level Netlist is functionally equivalent to the RTL.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e43891a0-ab09-4df2-898d-7e843158e936)

* The fundemental building blocks which are the standard cells have regular layouts.
* Each cell has different views/models which are utilised by different EDA tools like liberty view with electrical models of the cells, HDL behavioral models, SPICE or CDL views of the cells, Layout view which include GDSII view which is the detailed view and LEF view which is the abstract view.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/48df884c-c894-4a2a-a511-09321c208d6b)

* Chip Floor Planning

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/38ecd866-ac83-42c7-83ba-2ba995f9ba4e)

* Macro Floor Planning

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/35ac760c-bba9-4bd1-9c65-e8ceeee2ccf5)

* Power Planning typically uses upper metal layers for power distribution since thay are thicker than lower metal layers and so have lower resistance and PP is done to avoid electron migration and IR drops.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/f18013a7-e4c7-4a6d-ba53-33362c04689a)

* Placement

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3654398b-40bc-4e42-9205-77f673d5584c)

* Global placement provide approximate locations for all cells based on connectivity but in this stage the cells may be overlapped on each other and in detailed placement the positions obtained from global placements are minimally altered to make it legal (non-overlapping and in site-rows)

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/817c504d-0b8e-4a0a-9c3c-e9d110c23535)

* Clock Tree Synthesis

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6db284d4-065f-450a-9200-a6e6cbfd7fbb)

* Clock skew is the time difference in arrival of clock at different components.
* Routing

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7458495f-b527-4f21-813e-8dbcbf29ed9b)

* skywater PDK has 6 routing layers in which the lowest layer is called the local interconnect layer which is a Titanium Nitride layer the following 5 layers are all Aluminium layers.

![stackup](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e4438c12-d83e-4083-a58f-33a410a47927)

* Global and Detailed Routing

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b54ebd4c-127a-441f-829e-6000531e9b8d)

* Once done with the routing the final layout can be generated which undergoes various Sign-Off checks.
* Design Rules Checking (DRC) which verifies that the final layout honours all design fabrication rules.
* Layout Vs Schematic (LVS) which verifies that the final layout functionality matches the gate-level netlist that we started with.
* Static Timing Analysis (STA) to verify that the design runs at the designated clock frequency.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d8bc72cd-2fe9-4ae2-9431-68a6fa77c671)

### Implementation

Section 1 tasks:- 
1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
2. Calculate the flop ratio.

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ DFF's = Flop\ Ratio * 100
```

* All section 1 logs, reports and results can be found in following run folder:

[Section 1 Run - 15-03_15-51](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-03_15-51)

#### 1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.

Commands to invoke the OpenLANE flow and perform synthesis

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```

Screenshots of running each commands

![Slide1](https://github.com/user-attachments/assets/a38ecd1f-ac82-4ba1-9b46-beafa83fbf38)
![Slide2](https://github.com/user-attachments/assets/620297fc-c6d3-4a3d-81b4-8ea187cb6f27)
![Slide3](https://github.com/user-attachments/assets/4495487f-56e6-4bbf-98f7-7ed1ed35d654)

#### 2. Calculate the flop ratio.

Screenshots of synthesis statistics report file with required values highlighted

![Screenshot from 2024-03-15 22-02-42](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9280fefc-80b2-44ef-af34-ef3bddd3c14e)
![Screenshot from 2024-03-15 22-03-39](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3275f46c-19d7-42c5-8984-96d455f6e09b)

Calculation of Flop Ratio and DFF % from synthesis statistics report file

```math
Flop\ Ratio = \frac{1613}{14876} = 0.108429685
```
```math
Percentage\ of\ DFF's = 0.108429685 * 100 = 10.84296854\ \%
```

## Section 2: task-2


# SKY130 Day 2: Good vs Bad Floorplan and Introduction to Library Cells(18/07/2025 - 20/07/2025)
## Chip Floor Planning Considerations
### Utilisation Factor and Aspect Ratio

### Theory
The first step in physical design is to **define the width and height of the core and die** : Beginning with a very simple netlist, that can extrapolated later we will first draw a basic diagram in the form of symbols that we will later convert into physical designs. We will take each cell (gates, specific cell like flip flop) and give it a standard (although rough for now) dimensions. As an example here, each unit will be 1 unit x 1 unit - i.e. 1 sq. unit in size, and since there are 4 gates/flip-flops here, the total size of the silicon wafer will 4 sq. units.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/bd876662-ea2d-4ca0-9393-39e2e34bdec2)


> NOTE : here, we are ignoring the wires

All logical cells will be placed inside the core - which is part of the die. If the logical cells occupy the core fully, it is known as 100% utilisation. Utilisation factor = Area occupied by netlist / Total area of core. In this case, we see that utilisation factor is 100%, but practically it is usually 50%. Aspect Ratio is the ratio between height and width. If the chip is square - it is 1, else the chip is rectangular in shape.

Example: 
{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/056fe880-4a00-4941-aab1-8e22c09e52c2)

Utilisation factor = 50 %

Aspect Ratio = 2 : 4 = 1 : 2 = .5


### Concept of Pre-Placed Cells

Pre-Placed cells are complex logic blocks that can be reused. They are already implemented and cannot be touched by Auto Place and Route tools - and hence are required to be very well designed. Placement of such cells are user-based. A combinational logic - such as netlist shown does a particular function and is composed of various gates. We can divide this logic into blocks - while preserving the connectivity of the logic. By extending IO pins and making connections we can convert the logic into two parts - that are blackboxed and can be used as needed. If a design only requires a black box, it can be directly handed over to the designer with out much hassle. The various preplaced blocks available include memory, clock-gating cell, comparator, MUX. The arrangement of these IPs in a chip are known as floorplanning.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/960cb6af-73a6-4fe9-ba92-5d658b41b8fb)

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/503e2a1f-ce46-4790-9260-6a2ce2b6f1ec)

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/ea9c5c91-9634-4a63-b022-24969a98a2d6)

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/2c193af2-6ff9-4533-8d6c-0c2e1833283f)


### De-Coupling Capacitors

We surround pre-placed cells with de-coupling capacitors. If we think of a circuit to be part of a block, whenever it is switched on there is a demand for current, which is supplied by the Vdd. Upon switching the circuit off, there is a discharge, which the ground accepts. However, practically when voltage is supplied is passes through a wire which causes it to reduce slightly due the resistance, inductance and capacitance in the wire, and the reduced voltage is called Vdd'. The Vdd' always needs to stay in the noise margin - which ranges from Vih to Voh. If this is not true, the circuit is unstable. This is due to the large physical distance between the actual voltage supply and the circuit.

Decoupling capacitors is a solution to this problem. Decoupling capacitors can be thought of as as a huge capacitor completely filled with charge. The equivalent voltage across the capacitor is same as across the main supply voltage. The capacitor decouples the circuit from the main supply. Hence, all the pre-placed cells get their power supply from the capacitors and hence are completely stable.

### Power Planning

Consider a particular piece of logic to be a _macro_, that is repeated many times on a single chip. It requires a lot of voltage, so voltage must be supplied through a decoupling capacitor. However, it is not feasible to add the de-coupling capacitors on the entire circuit - only critical elements can be decoupled.

If the 16 bit bus is connected to an inverter, then it means that all the capacitors will discharge the voltage at once. A lot of capacitors discharging at once cam cause **Ground Bounce** due to great amount of voltage needed to drained at the same time, and turning the capacitor on might cause **Voltage Drop** due to insufficient current. Ground bounce and voltage drop might cause the voltage to not be within the noise margin range. To solve this problem, we can have multiple powersource taps and sources ( known as a power mesh) where capacitors can source current from the nearest Vdd and sink current to the nearest Ground.

### Pin Placement and Logical Cell Placement Blockage

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/92ccc847-3206-4223-b279-f73045b7d0e5)

Take the above netlist as an example needing to be implemented. The information about the connections is coded through VERILOG (also known as VHDL).The input and output ports are placed left and right between the core and the die respectively. The placements of the ports is cell-specific. The clocks are continuously drive the cells and hence clock ports are bigger than data ports. Due to this, we also need the least resistance paths for the clocks. The size is inversely proportional to the resistance.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/2d72b528-89f5-42d4-bb11-5a183b37113b)

After the pin placement, we create Logical Cell Placement Blockage to ensure that the APR tool does not place any cell on the pin locations.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/f87544bd-7fb1-422d-9229-d885444d6c89)


### Implementation

Section 2 tasks:- 
1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
2. Calculate the die area in microns from the values in floorplan def.
3. Load generated floorplan def in magic tool and explore the floorplan.
4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
5. Load generated placement def in magic tool and explore the placement.

```math
Area\ of\ die\ in\ microns = Die\ width\ in\ microns * Die\ height\ in\ microns
```





#### 1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.

Commands to invoke the OpenLANE flow and perform floorplan

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```

Screenshot of floorplan run
![Slide3](https://github.com/user-attachments/assets/4cda4078-e7fa-43e7-bde7-5d2c3608bdfa)
![Slide4](https://github.com/user-attachments/assets/479b73a2-8fa2-484f-8c29-417bbeea3050)
![Slide5](https://github.com/user-attachments/assets/827ff0bc-4dae-44c9-8841-e2dbf292bf0d)

#### 2. Calculate the die area in microns from the values in floorplan def.

Screenshot of contents of floorplan def

![Slide6](https://github.com/user-attachments/assets/b7fa29ff-109d-4bd6-9dc5-65904fc2530d)

According to floorplan def
```math
1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Square\ Microns
```
## Library Binding and Placement
### Netlist Binding and Initial Place Design

+ The first step is to bind the netlist with physical cells i.e. cells with real dimension. The netlist contains various gates, that while in the schematic are of a certain shape as depicted, are usually square/rectangular in shape in production. These gates are given a specific shape, and in the end look very different from the netlist.

These blocks are sourced from a "_shelf_", known as a **library**. The library has cells with various shapes, dimensions and also contains information about the delay information. The library contains various sizes of cells with the same functionality too - since bigger cells have lesser resistance

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/73dae3fe-cf37-41dc-8ef5-20d2d00ad475)

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/a2e71ed5-14fc-4ff9-b1c1-47d92af242b5)

+ The second step is **PLACEMENT**, which is done based on connectivity. As can be seen, flip flop 1 is close to the  _Din1_ pin and flip flop 2 is close to _Dout1_ pin. Combinational cells are placed in close proximity to FF1 and FF2 as to reduce delay.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/1b63d280-f78d-4c4d-aa86-dcf609429bd7)


### Optimise Placement Using Estimated Wire-Length and Capacitance

Here, we will estimate wirelength needed to connect the components together. If the wirelength is too long, we would need to install repeaters, as the signal may change over a long distance. Repeaters essentially recondition the same signal to it's prior strength.

### Final Placement Optimization

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/0941c315-195a-43f7-89aa-70e5e3215443)

### Congestion Aware Placement Using RePLACE

The command to run placement of OpenLANE - _run_placement_ is a wrapper which does three functions
- Global Placement (by using the RePlace tool) - there is no legalisation and HPWL reduction model is used
- Optimization (by Resier tool)
- Detailed Placement (by OpenDP tool) - legalisation occurs - where standard cells are placed in rows and there will be no overlap of the cells.

Placement aims to **converge the overflow value**. 

> NOTE: If placement will be sucessful and the designs will converge, the overflow value will progressively reduce during the placement.


#### 3. Load generated floorplan def in magic tool and explore the floorplan.

Commands to load floorplan def in magic in another terminal

```bash
# Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/floorplan/

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

Screenshots of floorplan def in magic

![Slide7](https://github.com/user-attachments/assets/aedc18fd-cee3-4161-8ed4-f13319912993)

Equidistant placement of ports

![Slide8](https://github.com/user-attachments/assets/34f3d804-418c-42ea-a408-ce92de2d49e8)

Diogonally equidistant Tap cells

![Slide9](https://github.com/user-attachments/assets/4dc0d9da-13ba-4bf9-a5e2-3035d8d7364d)













#### 4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.

Command to run placement

```tcl
# Congestion aware placement by default
run_placement
```

Screenshots of placement run

![Slide10](https://github.com/user-attachments/assets/9e8df9c3-cc83-4c9c-854a-8493181f3b89)
![Slide11](https://github.com/user-attachments/assets/e9b13be1-6e84-46a0-ab39-606f5df12aa6)

#### 5. Load generated placement def in magic tool and explore the placement.

Commands to load placement def in magic in another terminal

```bash
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

Screenshots of floorplan def in magic

![Slide12](https://github.com/user-attachments/assets/c0658470-aa95-4906-95d3-b820e560aa17)

Standard cells legally placed 

![Slide13](https://github.com/user-attachments/assets/7f4cd375-c6c9-4f0a-98b6-2817b75b18ee)

Commands to exit from current run

```tcl
# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```
## Cell Design and Characterisation Flows
### Inputs for Cell Design Flow and Circuit and Layout Design Step

Standard cells - for example AND gate, OR gate, BUFFER etc are stored in the _standard cell library_. There are various types of cells in the library with various variations as well - in drive strengths, functionality, and voltages. For a greater cell size, there is greater drive strength for longer wires. If there is high Vth, then it will take more time to switch than a lesser threshhold voltage cell.

The standard cell design flow is as follows:-

INPUTS (PDKS : DRC and LVS rules, SPICE models, library and user defined specs)

PROCESSES (circuit, layout design and charecterisation)

OUTPUTS (Circuit Description Language, GDSII, lef, timing, noise etc)

> DRC & LVS Rules contain tech files and poly substrate parameters
> 
> SPICE Models contain threshold, linear regions, saturation region equations with added foundry parameters, including NMOS and PMOS parameters
> 
> User defined specifications include cell height and cell width, supply voltage, pin locations, and metal layer requirement
> 
>  IMPORTANT: The standard cell library developer must adhere to the rules given by the foundry so that when the cell can be used on a real design without any errors
>
> Circuit design is done by modeling the pmos and nmos to meet input library requirement
> 
> Layout design is done using Euler's path and stick diagram on Magic layout tool
>
> {IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
> 
> ![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/b94b535f-ebd1-4b8a-bd36-f649fb6a753f)

### Typical Characterisation Flow

Steps of Characterisation Flow:-

1) Reading of SPICE module files
2) Reading of netlist extracted by SPICE
3) Recognising buffer behaviour
4) Reading subcircuits
5) Attaching neccessary power sources
6) Applying stimulus
7) Provision of of neccessary output capacitance
8) Provision of simulation command

These steps are given to the CHARECTERISATION SOFTWARE KNOWN AS **GUNA** in the form of a configuration file, which will generate timing, noise and power models in the form of _.libs_ files.

## General Timing Characterisation Parameters
### Timing Threshhold Definitions

Here, we will talk about the semantics of the various _.libs_ files generated by GUNA. To do this, we will take this circuit as an example:

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/0ed894da-ff96-46f5-8e9e-3b3271884568)

Here, the red line is output of first inverter and blue is output of second inverter.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/07cc3660-34e2-4446-8d50-97599d213504)

{IMAGE CREDITS: DEEPTHY SANTHAKUMAR}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/198064dc-3dd9-4bf5-aa52-d0012d7544f9)

{IMAGE CREDITS: DEEPTHY SANTHANKUMAR}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/aa2d9663-c41d-45df-b74e-de6f4bd2de86)

### Propogation Delay and Transition Time

Propogation delay is calculated as = time(out_x_thr) - (time_x_thr). If the propogation delay is negative, it can cause quite unexpected results - as an output is generated before the input. Hence, threshhold values should be selected properly. Delay threshold is usually 50% and slew rate threshold is usually 20%-80%.

Transition time is calculated as = time(slew_high_x_thr) - time(slew_low_x_thr)

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/68f7dbf3-b2e1-4be0-977c-6a6ef80f69b6)

## Section 3 - Design library cell using Magic Layout and ngspice characterization (21/07/2025 - 23/07/2025)

### Theory

## Labs for CMOS Inverter NGSPICE Simulations
### IO Placer Revision

OpenLANE configurations can be changed inside the shell itself, on the fly. IO Mode is usually set to _random equidistant_. However, if we want to change this, we can do so through the following command typed after floorplan : **set ::env(FP_IO_MODE) 2**. After running this command, the IO [input - output] pins will not be equidistant in mode 2 (instead of the default - that is 1). 

After this, we may re-run floorplan, and then check by seeing that the pins are placed based on of Hungarian algorithms now i.e. stacked one over the other. 

> NOTE: changing the configuration on the fly will not change the runs/config.tcl, the configuration will only be available on the current session.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/64fccafc-180a-4e66-881a-80fabe083dc1)

### SPICE Deck Creation For CMOS Inverter

The SPICE deck contains connectivity information about netlists, inputs to be provided, TAPS for the outputs etc. The component values are taken, that are usually -: for the PMOS it is .375u/.25u (i.e. the channel length is .25 micron and and the channel width is .375 micron). Ideally, the PMOS should be 2 to 3 times wider than the NMOS. This is as the PMOS hole carrier is slower than the NMOS carrier, and since the rise and fall time must be matched, to reduce the resistance, we increase the width of the PMOS. The next steps are to identify and name the nodes:

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/e85697ff-266b-4fc5-83a9-c3fe0143ffcf)

The syntax of the SPICE deck netlist PMOS and NMOS is _[component name] [drain] [gate] [source] [substrate] [transistor type] W=[width] L=[length]_. It is to be noted that all components in a netlist are described based on its node and values.

> EXAMPLE SYNTAX - M1 OUT IN VDD VDD PMOS W=.375U L=.25u

### SPICE Simulation Lab for CMOS Inverter

The start of SPICE simulation is _.op_ where in Vin will be swept from 0 to 2.5 with 0.05V steps. The model file is **tsmc_025um_model.mod** that has all the technological parameters for the 0.25µm NMOS and PMOS.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/bdec7a54-4667-4c1f-acbc-193062f2bcda).

For SPICE simulation, there are various steps-:

1) Open the NGSPICE simulator
2) Source the Circuit File through _source_ command
3) Execute it by the command _run_ and then use _setplot_ which allows one to view any plots possible from the simulations specified in the spice deck and will give you a choice for which simulation to be run
4) Then, type _display_ which will give you a choice of nodes to be plotted which when _plot out vs in_ is typed will be plotted on a graph.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/a4931bc2-cb5d-4e9e-8c14-54bc916c0b00)

### Switching Threshhold Vm

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/da38d8fa-1309-485b-b68d-e0e35c819a0a)

POINTS TO BE NOTED:

- The shapes of the graphs are almost the same, through which we can derive the conclusion that CMOS is a robust device
- The parameters that determine the robustness of the CMOS is the switching threshhold and the propogation delay

The Switching Threshhold is the point where the the input voltage is equal to the output voltage and both PMOS & NMOS are in saturation region. When these are turned on, there is a high chances of leakage and  that the current flows directly from VDD to GND. Due to this, short circuit can be seen.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/07f581e6-f0c1-49b3-b190-18c4d5a05157)

### Static and Dynamic Simulation of CMOS Inverter

To find Vm, we use DC TRANSFER ANALYSIS. Simulation is essentially a sweep from 0V to 2.5V by taking 0.05V steps.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/7709cad2-6227-4878-baad-d3165745ef67)

To find propogation delay, we use transient analysis when a pulse is applied to the CMOS.

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/1797489d-2861-4149-879b-496c616550db)

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/9dda14bc-11c3-4469-9d27-4ad812765df2)

### Lab Steps to GitClone VSDSTD Cell Design

We have been provided with a github repository wherein inverter files lie. It is available at this link - https://github.com/nickson-jose/vsdstdcelldesign. Steps to clone and observe the layout are as follows:
1. Clone the custom inverter standard cell design from the github repository shared above
2. Clone the repository with the custom inverter design through the command _git clone https://github.com/nickson-jose/vsdstdcelldesign_
3. Subsequently, copy the tech file to the _vsdstdcelldesign_ directory (created through above step) by this command _cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/_
4. Then, open the custom inverter layout in MAGIC through this command: _magic -T sky130A.tech sky130_inv.mag &_cp__

{IMAGE CREDITS: AUTHOR ; SCREENSHOT TAKEN FROM DEVICE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/307eb43f-4fe3-4d28-bca0-4e495d171489)

## Inception of Layout and CMOS Fabrication Process

The 16 MASK CMOS Fabrication process is as follows:

### Create Active Regions

1. The first step is to select a substrate - which is where the entirety of your design is fabricated. The most common substrate is a P doped Silicon Substrate. A substrate is ideally lesser doped than it's wells.

2. The next step is creating an active region for transistors. It is to be noted that it is necessary to have isolation between the pockets, which can be done through
   - Growing 40nm of Silicon Dioxide
   - Depositing 80nm of Silicon Nitride.
   - Depositing a layer of photoresist
   - Deposit mask-1 layer on top of photoresist. It covers the photoresist layer that must not be etched away (protects the two transistor active regions)
   - Applying UV light to remove the layers on the unmasked regions
   - Removing mask-1 and photoresist layers
   - Placing the chip in the furnace to grow the oxide in other areas
   - Removing the Si3N4 layer using hot phosphoric acid to have only p-substrate and SiO2 left

### Formation of N and P well

3. P well and N well formation
    + Deposition of photo resist layer and define the areas to protect by deposition of mask-2 and 3. Mask 2 protects the N-Well (PMOS side) while P-Well (NMOS side) is being fabricated and Mask 3 protects P-Well while N-Well is being formed
    + Application of UV Light to remove the exposed photoresist
    + Placing of chip in furnace to diffuse the boron and phosphorous to form wells. This process is called **Twintub** process.

> Boron [B] is used to form P-Well and Phosporus [P] is used to form N-well

### Formation of Gate Terminal

Gate Terminal is where Threshhold Voltage is controled - as seen below:

{IMAGE CREDITS: VSDIAT ; SCREENSHOT TAKEN FROM LECTURE}
![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/2803bfef-5a63-4e51-a91f-ca5f3bd2f3c5)

4. Formation of Gate
     + Deposit photo resist layer to define the areas to be protected, and then subsequently deposit mask-4. Then, UV light is applied, and the exposed area of photoresist is removed
     + Then, implantation of  low energy boron at the surface of p-well using mask-4 to control the threshold occurs
     + Similarly, implantation of phosphorous/arsenic for n-well using mask-5 occurs
     + Fixing the oxide which is damaged by implantation steps by removing extra SiO2 using the hydroflouric acid and re-grow high quality SiO2 on p-substrate to contol the oxide thickness occurs next
     + Addition of polysilicon film subsequently occurs
     + Then, mask-6 is added and etching using photolithography occurs
     + Then, mask 6 is etched off to form the gate terminal

### Lightly Doped Drain [LDD] Formation

5. LDD Formation - the reason LDDs are created is to prevent the hot electron which can eventually cause Si - Si bonds break or create voltage that passes the 3.2eV barrier leading to issues with doped regions. The second major need is to prevent another effect, known as the short channel effect which can cause gate malfunctioning due to the drain field penetrating the channel.
     + Mask 7  and 8 are created for NMOS (lightly doped N-type) and PMOS (lightly doped P-type) respectively.
     + Heavily doped impurity (N+ for NMOS and P+ for PMOS) are added for the actual source and drain but the lightly doped impurity which are also added help maintain spacing between the source and drain and prevent hot electron effect and short channel effect.
     + To protect the lightly doped regions, we also add SiO2 and create spacers using _plasma anisotropic_ etching

### Source and Drain Formation

6. Source and Drain Formation
     + Thin screen oxide is added to avoid channeling during. Channeling is when implantations dig too deep into substrate which is very problematic
     + We create Mask-9 is for N+ implantation and Mask-10 for P+ implantation
     + The side wall spacers maintain the N-/P- while implanting the N+/P+
     + High temperature annealing is done as well

### Local Interconnect Formation

7. Steps to Form Connects and Interconnects [LOCAL] - these are very important as they help in controlling the electrical charecteristics. These are also the only things accessible to the end user.
     + The thin screen oxide is removed for opening up the source, drain and gate for contact building. We use Titanium as it has less resistance.
     + Titanium Diselenide [Ti2Si2] is used for local interconnects
     + Mask 11 is formed and Titanium Nitride [Ti N] is etched off by RCA cleaning to create the first level contact

### Higher Level Metal Formation

8. Higher Level Metal Formation - These steps are very similar to the previous steps and are quite easy to understand.
     + The previous steps in the MASK process have created an uneven surface layer. A layer of Silicon Dioxide [SiO2] doped with phosphorous or boron -[boron reduces the temperature] [known as phosphosilicate glass and borophosphosilicate glass] is deposited on the wafer surface.
     + Then, the surface is polished using the CMP [Chemical Mechanical Polishing] technique to planarize the surface.
     + Contact holes are created through photolithography.
     + Various masks are used for the various processes after this:-
          - Mask 12 is created for the first contact holes
          - Mask 13 is used for the first Aluminum contact layer, which the contact holes are connected to.
          - Mask 14 creates the second contact holes
          - Mask 15 is similarly, for the second Aluminum contact layer
          - Finally, we use Mask 16 for making contact to topmost layer

### Lab Introduction to SKY130 Basic Layers Layout and LEF using Inverter

{IMAGE CREDITS: DEEPTHY SANTHAKUMAR}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/c4eb61e9-abe9-40fb-8191-0a032c8cd91c)

> In sky130A, the first layer is the LDD or local-i and then the m1, m2 layers and so on.
> The power and ground lines are located in m1.
> When polysilicon crosses ndiffusion then NMOS and if polysilicon crosses pdiffusion then PMOS is created.
> The output of the layout is the _LEF_ file, which is used by the router in APR to get the location of standard cell pins for proper routing. So it is essentially an abstract form of the layout of a standard cell.

### Implementation

* Section 3 tasks:-
1. Clone custom inverter standard cell design from github repository: [Standard cell design and characterization using OpenLANE flow](https://github.com/nickson-jose/vsdstdcelldesign).
2. Load the custom inverter layout in magic and explore.
3. Spice extraction of inverter in magic.
4. Editing the spice model file for analysis through simulation.
5. Post-layout ngspice simulations.
6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

* Section 3 - Tasks 1 to 5 files, reports and logs can be found in the following folder:

[Section 3 - Tasks 1 to 5 \(vsdstdcelldesign\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign)

* Section 3 - Task 6 files, reports and logs can be found in the following folder:

[Section 3 - Task 6 \(drc_tests\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/drc_tests)

#### 1. Clone custom inverter standard cell design from github repository

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of commands run

![Slide14](https://github.com/user-attachments/assets/df7b665c-b97c-44fb-b2f6-5f0d7973a337)

#### 2. Load the custom inverter layout in magic and explore.

Screenshot of custom inverter layout in magic

<img width="1366" height="768" alt="Capture-0 1" src="https://github.com/user-attachments/assets/509cc8a0-6a16-47c9-9ffa-888cf6ac807d" />

NMOS and PMOS identified

<img width="1366" height="768" alt="Capture-0 2" src="https://github.com/user-attachments/assets/efb6a4d0-ed1c-4188-ad97-a6fd61dcc8bb" />


Output Y connectivity to PMOS and NMOS drain verified

<img width="1366" height="768" alt="Capture-0 3" src="https://github.com/user-attachments/assets/482b72fa-6c00-4a7f-95be-607275a2fbde" />

PMOS source connectivity to VDD (here VPWR) verified

![Screenshot from 2024-03-19 00-34-11](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/173efda1-d5d1-49d9-a040-771092b1e55b)

NMOS source connectivity to VSS (here VGND) verified

![Screenshot from 2024-03-19 00-36-09](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/107a8e0b-43de-4b5d-90fe-516ea83673b1)

Deleting necessary layout part to see DRC error

![Screenshot from 2024-03-19 01-10-28](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/861912e4-eef9-4226-b563-db7f49ca6632)

#### 3. Spice extraction of inverter in magic.

Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic

```tcl
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```

Screenshot of tkcon window after running above commands

<img width="1366" height="768" alt="Capture-0 2" src="https://github.com/user-attachments/assets/e1154baa-30fc-4120-af93-33cf3742eac5" />

Screenshot of created spice file

<img width="832" height="451" alt="image" src="https://github.com/user-attachments/assets/3d9fb589-30ba-449b-8cb9-e6cb02d705f4" />

#### 4. Editing the spice model file for analysis through simulation.

Measuring unit distance in layout grid

<img width="831" height="461" alt="image" src="https://github.com/user-attachments/assets/8baf0dee-dca6-4121-93d2-b269950e94aa" />

Final edited spice file ready for ngspice simulation

<img width="830" height="453" alt="image" src="https://github.com/user-attachments/assets/8a096630-776d-4ffc-a0a0-be5b74c61b8d" />
<img width="832" height="449" alt="image" src="https://github.com/user-attachments/assets/c8045828-a80c-4810-9789-7ad5ad867cd7" />

#### 5. Post-layout ngspice simulations.

Commands for ngspice simulation

```bash
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
```

Screenshots of ngspice run

<img width="1366" height="768" alt="Capture0" src="https://github.com/user-attachments/assets/a14faee2-8b54-4712-ba8c-ee36d9835d38" />
<img width="1353" height="768" alt="Capture2" src="https://github.com/user-attachments/assets/8e15e7d0-2067-461e-a498-b075fe3d2762" />


Screenshot of generated plot

<img width="1366" height="766" alt="Capture1" src="https://github.com/user-attachments/assets/b19b911c-c117-41e2-b11a-fb71d8779868" />

Rise transition time calculation

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```
20% Screenshots

<img width="1366" height="768" alt="Capture3" src="https://github.com/user-attachments/assets/57b2b3a6-98bc-48c6-96c9-9efb91b5c3d2" />
<img width="1366" height="768" alt="Capture4" src="https://github.com/user-attachments/assets/255f6f26-268d-4ea4-a2b4-8bdd6f5b8380" />

80% Screenshots

<img width="1366" height="768" alt="Capture5" src="https://github.com/user-attachments/assets/74f8c7d3-d02a-40b7-b10f-2eb95f25ffb9" />
<img width="1366" height="768" alt="Capture6" src="https://github.com/user-attachments/assets/0e8ad547-caf3-4a16-98fe-9c263a1d2426" />

```math
Rise\ transition\ time = 2.24638 - 2.18242 = 0.06396\ ns = 63.96\ ps
```

Fall transition time calculation

```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

20% Screenshots

<img width="1366" height="768" alt="Capture7" src="https://github.com/user-attachments/assets/d9e66806-a068-4f54-8efd-7cd0ba5fa43e" />
<img width="1366" height="768" alt="Capture8" src="https://github.com/user-attachments/assets/7bba4455-6956-4042-8a13-e74db2193218" />

80% Screenshots

<img width="1366" height="768" alt="Capture9" src="https://github.com/user-attachments/assets/aca0cf82-c4db-4fdd-9a14-aaa5fda04b6f" />
<img width="1366" height="768" alt="Capture10" src="https://github.com/user-attachments/assets/a55e0816-1b0c-4b0f-ae13-905011f172f0" />

```math
Fall\ transition\ time = 4.0955 - 4.0536 = 0.0419\ ns = 41.9\ ps
```

Rise Cell Delay Calculation

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% Screenshots

<img width="1366" height="768" alt="Capture11" src="https://github.com/user-attachments/assets/c6243d16-34ae-40a8-a797-7442398879c4" />
<img width="1366" height="768" alt="Capture12" src="https://github.com/user-attachments/assets/9563ed79-daf5-4c87-b20e-58177cd25d11" />

```math
Rise\ Cell\ Delay = 2.21144 - 2.15008 = 0.06136\ ns = 61.36\ ps
```

Fall Cell Delay Calculation

```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% Screenshots








#### 6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Link to Sky130 Periphery rules: [https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html](https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html)

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```bash
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
```

Screenshots of commands run

<img width="1366" height="767" alt="Capture13" src="https://github.com/user-attachments/assets/95da7bc9-c896-4c44-ac1d-b1c5550e8b3f" />
<img width="1366" height="768" alt="Capture15" src="https://github.com/user-attachments/assets/650ebff6-ccc1-4c6e-9631-debd149eeb8b" />

Screenshot of .magicrc file

<img width="1353" height="754" alt="Capture14" src="https://github.com/user-attachments/assets/e7e81117-d85b-4ccc-8094-c9d1f0cc0301" />

**Incorrectly implemented poly.9 simple rule correction**

Screenshot of poly rules

<img width="831" height="456" alt="image" src="https://github.com/user-attachments/assets/323eac0a-71d7-4747-b7e0-fa4e2dab5a6f" />

Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u

<img width="749" height="420" alt="image" src="https://github.com/user-attachments/assets/3c6a47bc-f0fc-461f-878d-57a06953d041" />
<img width="745" height="420" alt="image" src="https://github.com/user-attachments/assets/0b739210-24f7-452b-a5bf-fac6109019ed" />

New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-03-21 23-58-44](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/dc30df54-3282-42f0-8e7d-fc4d8877ed64)
![Screenshot from 2024-03-21 23-09-50](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d112ca07-854c-41e7-8822-c269e21defea)

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![Screenshot from 2024-03-21 23-13-11](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b18e8e07-ef0f-40fb-9b6d-8aae878a23c6)
![Screenshot from 2024-03-22 00-00-40](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d5afe8d8-691b-485d-a89a-8f901e18b56e)

**Incorrectly implemented difftap.2 simple rule correction**

Screenshot of difftap rules

![Screenshot from 2024-03-22 00-14-47](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/086b7a66-b60a-470a-b5c0-a5ac938ebec3)

Incorrectly implemented difftap.2 rule no drc violation even though spacing < 0.42u

![Screenshot from 2024-03-22 00-14-36](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a2d0d739-2df5-4eb5-ab78-c80d366e24e4)

New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-03-22 00-26-43](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b5892f9b-9c5d-4b1b-baa2-6fe45f3965b1)

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![Screenshot from 2024-03-22 00-29-22](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a3f92160-6701-48fb-b6cf-e4c41dc4a531)

**Incorrectly implemented nwell.4 complex rule correction**

Screenshot of nwell rules

![Screenshot from 2024-03-22 00-51-34](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/4ad4901d-0b9a-4339-89e3-7bb3fce2766d)

Incorrectly implemented nwell.4 rule no drc violation even though no tap present in nwell

![Screenshot from 2024-03-22 00-52-51](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/87da8944-0ad8-455d-97ec-3909eac656c3)

New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-03-22 01-03-42](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/886c6930-6314-4a6f-97d9-6b8423444ac0)
![Screenshot from 2024-03-22 01-04-04](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d9808e9a-42c2-4421-9b82-2ef65a5a1ad7)

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![Screenshot from 2024-03-22 01-10-25](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/49b1004d-f860-4ca7-86f4-4d79784a01cf)

## Section 4 - Pre-layout timing analysis and importance of good clock tree (24/07/2025 - 26/07/2025)

### Theory
(This section contains only essential theoretical information related to the task before the lab steps)
## Timing Modelling Using Delay Tables
### Lab Steps To Convert Grid Information Into Track Information

_sky130_inv.mag_ located in _vsdstdcelldesign_ directory contains all information like PG and port information, logic etc. OpenLANE is a PnR tool and hence does not require the full information present in the _.mag_ file. The only information that we require are the boundary, power and ground rails, and the inputs & outputs information. This is the reason of we use **.lef** files. Hence, our next  objective is to extract the LEF file from the MAGIC file and plug that into the picorv32a design. The guidelines to be followed while making a standard cell are -:

1. The input and output ports must lie at the intersection of the horizontal and vertical tracks (this is to ensure the routes can reach the ports).
2. The width and height of the standard cell must be odd multiples of the track's horizontal and vertical pitch respectively

## Timing Analysis With Ideal Clocks Using Open STA
### Setup Timing Analysis And Introduction to Flip-Flop Setup Time

Consider an ideal clock [i.e. the clock tree is not built yet] where perform timing analysis to understand the parameters [later the same can be done using real clocks]. Specifications are as mentioned in the picture [Clock frequncy (F) is 1GHz and clock period (T) is 1ns]. -:

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/39437ad9-3953-4955-ac5f-e15c60e3adf0)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/f12cdcd3-e080-4d25-977c-aed998a2e060)

The setup timing analysis equation is = Θ < T - S

> Θ = Combinational delay which includes clk to Q delay of launch flop and internal propagation delay of all gates between launch and capture flop
> 
> T = Time period, also called the required time
> 
> S = Setup time. As demonstrated below, signal must settle on the middle (input of Mux 2) before clock tansists to 1 so the delay due to Mux 1 must be considered, this delay is the setup time.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/0f2910d0-0c34-40f1-aaf5-40c311efe669)

### Introduction to Clock Jitter and Uncertainty

CLK signals are sent to the device by the PLL (Phase Locked Loop). This clock source is expected to send clock signal at 0, T, 2T etc. However, even these clock sources might or might not be able to provide a clock **exactly** at Tns because of its own in-built variation known as jitter. Jitter can be thought of as short-term fluctuations in the timing of signal transitions, which can result in deviations from the expected clock or data timing.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/a298949c-3101-44c3-b15a-d60efbc9eca8)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/ca549e3e-4895-4a62-b3e6-4924e2394d2d)

Hence, we see that a more realistic equation for setup time is = Θ < T - S - SU

> SU = Setup uncertainty due to jitter which is temporary variation of clock period, which is due to non-idealities of PLL.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/48e91fce-8564-4295-9b94-4b50afa9288f)

### Lab Steps to Configure OpenSTA for Post-Synth Timings Analysis

STA can either be -:
+ single corner - which only uses the LIB_TYPICAL library which is the one used in pre-layout(pos-synthesis) STA
+ multi corner - multicorner which uses LIB_SLOWEST(setup analysis, high temp low voltage),LIB_FASTEST(hold analysis, low temp high voltage), and LIB_TYPICAL libraries

1. In the location *Desktop/Work/tools/openlane_working_dir/openlane_ there is a file named *pre_sta.conf* on which we will be doing the prelayout analysis. The file contains the following contents-:

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE AND SUBSEQUENTLY MODIFIED FOR MORE CLARITY}

![drawn](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/11cfc5f7-384f-4991-90ea-b8957b2afb74)

2. This is the SDC file on which analysis will be done is located at *Desktop/Work/tools/openlane_working_dir/openlane/designs/picorv2a/src* and is named *my_base.src_. It contains the following contents -:

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE AND SUBSEQUENTLY MODIFIED FOR CLARITY}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/053fee45-34e9-4e2a-9b11-fa496c0fcb4e)

3. The various commands to be run and their functions are -:

   + _create_clock_ -it creates clock for the port with specified time period.
     
   + *set_input_delay* and *set_output_delay* - defines the arrival/exit time of an input/output signal relative to the input clock. [This is the delay of the signal coming from an external block and internal delay of the signal to be propagated to external ports] This adds a delay of Xns relative to clk to all signals going to input ports, and delay of Yns relative to CLK to all signals going to output ports.
     
   + *set_max_fanout* - specifies maximum fanout count for all output ports in the design.
     
   + *set_driving_cell* - models an external driver at the input port of the current design.
     
   + *set_load* sets a capacitive load to all output ports.

4. Execute *sta pre_sta.conf* and check timing.

### Lab Steps to Optimize Synthesis to Reduce Setup Violations

To reduce negative slack, focus on large delays. Net with big fanout might cause delay increase. Use report_net -connections <net_name> to display connections. First thing we can do is to go back to OpenLane and reduce fanouts by setting ::env(SYNTH_MAX_FANOUT) 4 then run_synthesis again.

For reducing the negative slack obtained, we must focus on the large delays and try to reduce them. Increases in delays are majorly caused by nets with big fanouts, which result in high load cap which causes high delay. To display the connections of the nets, the commands **report_net -connections <net_name>** can be used. Now, looking upon this output, we realise that fanouts must be reduced. This can be done by going back to OpenLANE and reducing fanouts by typing **::env(SYNTH_MAX_FANOUT) 4**. After this, we can run_synthesis again and obtain a expected value for slack.

### Lab Steps to do Basic Timing ECO

However, if we want to reduce the negative slack even more, we can upsize the cells with high fanouts so that bigger drivers will be used. Now, since we cannot change load capacitance but can change the cell size, we can increase the size of the cell for a large driver to drive large cap loads leading to lesser delay. This is often done in iterations until we reach the desired slack in a process known as Timing ECO [Engineering Change Order]

## Clock Tree Synthesis TritonCTS and Signal Integrity
### Clock Tree Routing and Buffering Using H-Tree Algorithm

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/b7ebc401-975d-4c82-94cb-980d7c724bb0)

Take into account the CLK port going to the various flip-flops in the above picture. It's purpose is to connect the port to the CLK pins of the many flip-flops based on the connectivity information given. In the above picture, we have blindly made connections and hence t2 is greater than t1. Skew is the difference between t2 and t1. CLK skew, as explained earlier, refers to the variation in arrival times of the clock signal at different points within a digital system. More simply, CLK skew is essentially the difference in propogation delay of the CLK signal as it moves along various paths. It can occur due to -:
- differences in wire lengths
- variations in signal routing paths
- variations in buffer delays
- other physical and environmental factors

Due to this, some parts of the system can recieve CLK signals earlier than or after the rest of the system. Minimizing clock skew is essential as to -:
- ensure proper synchronization of signals
- reliable operation of the digital circuit.

> NOTE : Ideally, the skew should be zero.

Now, since the skew is not minimum, or even close to minimum in the above picture, we can call this tree a **_bad tree_**. To optimize this scenario, we can use H-Tree routing. It analyses the clock route by calculating the distance from the source to all the endpoints and deciding on a midpoint to start building tree. Subsequently, it finds another midpoint and creates divergents in the wire. Eventually, after repeating this process, the CLK reaches all the flip-flops at almost the same time, while splitting up at various midpoints.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/0fdaf27e-01a3-4ba6-b32b-5bc4d4a6beaf)

It is expected that the input CLK signal is exactly reproduced at the output. However, this does not happen in H-Tree routing due to inherent resistance and capacitance in physical wires, which may cause the signal to experience distortion. We can solve this problem by inserting buffers/repeaters along the path for signal integrity. In the past, we have also talked about another kind of repeaters, used in data paths. The key differences between repeaters used in clock and data paths respectively lie in their **rise and fall times**. Clock buffers have **same rise and fall times**, to ensure uniform signal propagation throughout the clock distribution network. Contrastingly, data buffers exhibit **varying rise and fall times**, which may differ based on the characteristics of the data being transmitted and the components involved in processing it.

### Crosswalk and Clock Net Shielding

Clock nets are critical nets in the design because clock tree is built is such a fashion that the skew is zero. There is a phenomenon called crosstalk where a signal transmitted on one channel  interacts with or interferes with signals on adjacent channels leading to distortion, noise, timing errors etc, which can cause the clock tree structure will be deteriorated. To solve this, all the clock nets are shielded [protected]. If there is a wire adjacent to such shields, then there exists a huge coupling capacitance causing two issues - (i) glitch and (ii) delta delay.

Whenever there is a switching activity happening in the aggressor, then the coupling capacitance is so strong that it directly affects the net close to it named _the victim net_, which is without any shielding. This causes a dip in the voltage, resulting in glitch. Due to a glitch, there can be incorrect data in memory, which can cause inaccurate functionality. To solve this, we do shielding which protects the victim nets by breaking the coupling capacitance between the aggressor and the victim. These shielding nets are either in the form of Vdd or Vss. The shields do not switch, and hence the victim will not switch as well.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/e19160f6-cd94-4572-9470-336db0ca6a7a)

### Lab Steps to run CTS using TritonCTS

After completion of Timing ECO, we see that the timing currently is still above 1. To reduce it, we can go through the results and switch the cells causing a lot of slack to buffers. After this the negative slack is reduced to below 1.  

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/cae7aaf6-c89f-4b6e-a631-7fbd4cdfe5e2)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/463cc177-c4da-428e-a2e4-fd5d751e0f73)


## Timing Analysis  With Real Clocks Using Open STA
### Setup Timing Analysis Using Real Clocks

Now the clock tree is built and timing analysis is done on real clocks.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/cc3c96ca-817f-4559-aefa-baa6a3583b78)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/bdd0b465-92b3-4d34-b389-eb0545d5048e)

> delta1 = launch flop clock network delay
>
> 
> delta2 = capture flop clock delay

Any design satisfying Slack [i.e. Data required time - Data arrival time] is ready to work in the given frequency. However, if this equation is violated, then slack will become negative which is not expected. We expect slack to be either zero or positive.

### Hold Timing Analysis Using Real Clocks

Hold Time is delay [time] needed by the MUX2 model within a flip-flop to transfer certain data outside. [i.e. how long it **holds** the data]. It is the time period during which the launch flop must retain dat before it reaches the capture flop. Unlike setup analysis, which has two rising clock edges, hold analysis occurs on the same rising clock edge for both the launch and capture flops. 

A hold violation occurs when the path is too fast, impacted by factors such as -:
 - combinational delay
 - clock buffer delays
 - hold time.
 
 > Notably, parameters such as time period and setup uncertainty hold no significance, as both launch and capture flops receive identical rising clock edges during hold analysis.

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/367dc2a4-b701-4ef6-9cf0-a6e2048b6564)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/3ed9941f-37df-4ec4-8dc7-28191831cdc1)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/5ad6901b-57b8-4d7a-a8f1-9215f70ca7d9)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/82b6ac76-15a9-4a0d-b496-76e1a9d3b012)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/f781227a-ddff-4d2a-8878-c54bb95127c6)

{IMAGE CREDITS: VSDIAT; SCREENSHOT TAKEN FROM LECTURE}

![image](https://github.com/ojasvi-shah/Advanced-Physical-Design-Using-OpenLANE--Ojasvi-Shah/assets/163879237/72ae228c-3900-494f-93ea-ffbd30880ad9)

### Implementation

* Section 4 tasks:-
1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
2. Save the finalized layout with custom name and open it.
3. Generate lef from the layout.
4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
6. Run openlane flow synthesis with newly inserted custom inverter cell.
7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

* Section 4 - Tasks 1 to 4 files, reports and logs can be found in the following folder:

[Section 4 - Tasks 1 to 4 \(vsdstdcelldesign\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign)

* Section 4 - Task 4 files, reports and logs can be found in the following folder:

[Section 4 - Task 4 \(src\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src)

* Section 4 - Task 5 files, reports and logs can be found in the following folder:

[Section 4 - Task 5 \(picorv32a\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a)

* Section 4 - Tasks 6 to 8 & 11 to 13 logs, reports and results can be found in following run folder:

[Section 4 - Tasks 6 to 8 & 11 to 13 Run \(24-03_10-03\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03)

* Section 4 - Tasks 9 to 11 logs, reports and results can be found in following run folder:

[Section 4 - Tasks 9 to 11 Run \(25-03_18-52\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52)

#### 1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.

Conditions to be verified before moving forward with custom designed cell layout:
* Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
* Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
* Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.

Commands to open the custom inverter layout

```bash
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd

![Screenshot from 2024-03-24 13-38-09](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2a35eb22-dd5f-4b67-9712-cbd2a84b526a)

Commands for tkcon window to set grid as tracks of locali layer

```tcl
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```

Screenshot of commands run

![Screenshot from 2024-03-24 13-49-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d0d9c106-4e05-4e73-a7ed-3f718cb69b42)

Condition 1 verified

![Screenshot from 2024-03-24 13-51-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b74b31c8-cdc7-4dcb-9467-5a1787bfa5fe)

Condition 2 verified

```math
Horizontal\ track\ pitch = 0.46\ um
```

![Screenshot from 2024-03-24 13-55-07](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e045e5b6-3592-4242-995d-de2049438ec5)

```math
Width\ of\ standard\ cell = 1.38\ um = 0.46 * 3
```

Condition 3 verified

```math
Vertical\ track\ pitch = 0.34\ um
```

![Screenshot from 2024-03-24 13-58-32](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a471b022-91ac-466a-8dd9-72b90f9c16c1)

```math
Height\ of\ standard\ cell = 2.72\ um = 0.34 * 8
```

#### 2. Save the finalized layout with custom name and open it.

Command for tkcon window to save the layout with custom name

```tcl
# Command to save as
save sky130_vsdinv.mag
```

Command to open the newly saved layout

```bash
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
```

Screenshot of newly saved layout

![Screenshot from 2024-03-24 14-33-20](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0beb4300-2ebc-4364-8e3d-37fdb6d52f5b)

#### 3. Generate lef from the layout.

Command for tkcon window to write lef

```tcl
# lef command
lef write
```

Screenshot of command run

![Screenshot from 2024-03-24 14-35-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6928c3dc-e633-414d-9ac1-71349cad4b9b)

Screenshot of newly created lef file

![Screenshot from 2024-03-24 14-37-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/15557990-33b4-4402-8c72-39b75da9ed07)

#### 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory

```bash
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Screenshot of commands run

![Screenshot from 2024-03-24 14-55-23](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/78559cee-ad3f-4301-83ae-df99f8417be3)

#### 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow

```tcl
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory

![Screenshot from 2024-03-24 15-29-56](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7b18f216-1160-4a65-91fd-998495ad3175)

#### 6. Run openlane flow synthesis with newly inserted custom inverter cell.

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshots of commands run

![Screenshot from 2024-03-24 15-36-46](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/4170c3c5-1a95-4165-9461-03b298cc20ef)
![Screenshot from 2024-03-24 15-37-32](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/8f52942c-4b28-4abd-b9a0-d48f20a8255f)
![Screenshot from 2024-03-24 15-37-44](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/47849bfd-dc47-4d9c-9077-7fb672df4ead)
![Screenshot from 2024-03-24 15-45-08](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0bc13ad3-d800-4681-b39d-8b64c9c9104f)

#### 7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

Noting down current design values generated before modifying parameters to improve timing

![Screenshot from 2024-03-24 16-00-18](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/33fe575a-7459-4c59-8329-f142ba2099e5)
![Screenshot from 2024-03-24 16-13-01](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/13e42f0a-69e7-410d-b901-bc6c4976b7e1)

Commands to view and change parameters to improve timing and run synthesis

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshot of merged.lef in `tmp` directory with our custom inverter as macro

![Screenshot from 2024-03-24 23-46-25](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/55de3fc6-498d-4456-8e79-ae6e175d2ca6)

Screenshots of commands run

![Screenshot from 2024-03-24 17-09-04](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/62209cce-90c2-4c52-a218-25805b57ef3f)
![Screenshot from 2024-03-24 17-09-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2d933bd5-a3b5-4d6d-a22f-5332bc3bf279)
![Screenshot from 2024-03-24 17-10-46](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a25b66af-9cf9-4ba9-adb6-f38ff85fa7cd)

Comparing to previously noted run values area has increased and worst negative slack has become 0

![Screenshot from 2024-03-24 17-11-08](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/81418082-747e-4702-b5ad-bb3e450eceb3)
![Screenshot from 2024-03-24 17-11-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a1bdb538-527c-4edd-877d-d4263e777321)

#### 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command

```tcl
# Now we can run floorplan
run_floorplan
```

Screenshots of command run

![Screenshot from 2024-03-24 17-12-09](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/10a18995-0b7c-4f44-8ef4-cca9239652da)
![Screenshot from 2024-03-24 17-37-50](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/72966b69-cea0-4ae7-8dc0-c7130a8c750a)

Since we are facing unexpected un-explainable error while using `run_floorplan` command, we can instead use the following set of commands available based on information from `Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl` and also based on `Floorplan Commands` section in `Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md`

```tcl
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```

Screenshots of commands run

![Screenshot from 2024-03-24 23-38-07](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/07534ca7-b0db-4ea2-bbcd-ea7d44241d6c)
![Screenshot from 2024-03-24 23-38-54](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c9705150-f953-4372-a811-88cae6378d2f)
![Screenshot from 2024-03-24 23-39-56](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c16bccc6-c650-4a65-b1de-7035609520d7)

Now that floorplan is done we can do placement using following command

```tcl
# Now we are ready to run placement
run_placement
```

Screenshots of command run

![Screenshot from 2024-03-24 23-49-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/12788798-aac5-4cfb-9254-69fb3d4e8e70)
![Screenshot from 2024-03-24 23-51-08](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/41eaeae7-d398-417c-b89f-e9014a92a699)

Commands to load placement def in magic in another terminal

```bash
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

Screenshot of placement def in magic

![Screenshot from 2024-03-25 00-16-54](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9cb8b463-a0dd-402f-b881-2504686b8d04)

Screenshot of custom inverter inserted in placement def with proper abutment

![Screenshot from 2024-03-25 00-00-10](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2fb0fc71-4784-4987-a55e-5d71dd35edbf)

Command for tkcon window to view internal layers of cells

```tcl
# Command to view internal connectivity layers
expand
```

Abutment of power pins with other cell from library clearly visible

![Screenshot from 2024-03-25 00-01-46](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b52d756d-430c-4e43-b514-db0084dc1794)
![Screenshot from 2024-03-25 00-05-35](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b8342668-c3fe-437e-b701-8c8be3740682)

#### 9. Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot

![Screenshot from 2024-03-26 05-52-18](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/790d4852-7f1d-47b5-a64f-5735f6064b61)

Newly created `pre_sta.conf` for STA analysis in `openlane` directory

![Screenshot from 2024-03-26 05-53-06](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0a02d055-f012-44bd-a750-4508bbfc771e)

Newly created `my_base.sdc` for STA analysis in `openlane/designs/picorv32a/src` directory based on the file `openlane/scripts/base.sdc`

![Screenshot from 2024-03-26 05-55-17](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/8c917d87-5507-4079-ba6b-facbf18c238f)
![Screenshot from 2024-03-26 05-55-38](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e07d05db-2f06-47ab-bff7-2af88c39d001)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

![Screenshot from 2024-03-26 06-04-28](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/32def177-5173-4dd7-ba3b-44e37846644c)
![Screenshot from 2024-03-26 06-05-07](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d8b8c46a-3a8b-458c-8c75-03f6577f5d17)
![Screenshot from 2024-03-26 06-05-53](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ab396c91-430f-41ca-b9a4-dda72a91c4d5)
![Screenshot from 2024-03-26 06-08-51](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/aa1d50b0-9cb1-45bf-a641-b64842166b48)

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis 

```tcl
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 25-03_18-52 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot

![Screenshot from 2024-03-26 06-20-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c5869cf5-ab95-46f9-9fd1-dc91e92455d8)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

![Screenshot from 2024-03-26 06-22-31](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0f3247fc-aaad-4e98-b23e-bdc9a361d08c)
![Screenshot from 2024-03-26 06-22-41](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9fcc3975-0e03-4515-aee5-04b7c1c6a315)
![Screenshot from 2024-03-26 06-22-50](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e19db773-3995-4af4-b0a3-188b02fdf454)
![Screenshot from 2024-03-26 06-23-01](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c22c85fb-1a94-4639-a731-da4c364d1a78)

#### 10. Make timing ECO fixes to remove all violations.

OR gate of drive strength 2 is driving 4 fanouts

![Screenshot from 2024-03-26 06-55-46](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/73c58332-a212-4a24-b853-e8cae3b385a6)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 07-02-44](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c50c6023-1836-468d-a8c3-955b02e4224c)
![Screenshot from 2024-03-26 07-04-08](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6059a511-9977-4d9e-8dde-8939f0e1b8f7)
![Screenshot from 2024-03-26 09-42-15](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/df3dba3c-9445-4d51-9842-bf4410f05cf5)
![Screenshot from 2024-03-26 07-07-50](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/f141d1ff-4e21-4f9a-ab47-19579a686ac4)

OR gate of drive strength 2 is driving 4 fanouts

![Screenshot from 2024-03-26 09-46-23](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3f66eed9-c43d-483e-ab85-21d70452b81f)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 09-49-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d896c1fa-078e-4fe1-8e4d-60fae870d672)
![Screenshot from 2024-03-26 09-50-13](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a21abd89-b92a-4d28-b065-6b8b523026de)
![Screenshot from 2024-03-26 09-50-33](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9b961126-3de7-450e-9789-5009ca7f6a16)

OR gate of drive strength 2 driving OA gate has more delay

![Screenshot from 2024-03-26 10-22-10](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7669eeef-7b93-4cfd-a152-17eec772496a)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11643_

# Replacing cell
replace_cell _14481_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 10-29-31](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c63cf6a1-582d-43e5-907f-e292b94cc086)
![Screenshot from 2024-03-26 10-29-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6495c2e8-78c8-41d2-b783-628f36b982c5)

OR gate of drive strength 2 driving OA gate has more delay

![Screenshot from 2024-03-26 10-32-27](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/4185dc98-a065-49d3-a92f-fb4b02f23ee5)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 10-36-59](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/be71b3a4-efe1-4239-be5a-28ccebd2b7f4)
![Screenshot from 2024-03-26 10-37-14](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2ae759b3-f9a7-478f-a34a-3f8706347eca)

Commands to verify instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

```tcl
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```

Screenshot of replaced instance

![Screenshot from 2024-03-26 10-43-04](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/970b3cb7-fe10-4b5e-99c9-85059714f8f2)

*We started ECO fixes at wns -23.9000 and now we stand at wns -22.6173 we reduced around 1.2827 ns of violation*

#### 11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use `write_verilog` and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist

```bash
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```

Screenshot of commands run

![Screenshot from 2024-03-26 10-54-15](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/90c90853-0664-44d7-8ff2-573621935870)

Commands to write verilog

```tcl
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

Screenshot of commands run

![Screenshot from 2024-03-26 11-02-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c6c8ce7f-5219-41bc-a5a8-47b0e1c62c7c)

Verified that the netlist is overwritten by checking that instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

![Screenshot from 2024-03-26 11-01-25](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/1ddb66da-64cb-426d-8d78-30370c63dacb)

Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```

Screenshots of commands run

![Screenshot from 2024-03-26 11-33-14](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a0f223bc-3cbb-4bb1-8c7e-d800f1a4efd7)
![Screenshot from 2024-03-26 11-33-22](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9bd610a8-fd5e-452b-94b2-5a5fc76db5e9)
![Screenshot from 2024-03-26 11-35-40](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/283d9b5e-fc48-45a3-8548-c68fc8966f46)
![Screenshot from 2024-03-26 11-36-16](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/af866818-af6f-4bc4-96c0-cf3c99839003)
![Screenshot from 2024-03-26 11-37-36](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/55aa5130-8a9f-48d6-abc8-7aace68b58c8)
![Screenshot from 2024-03-26 11-38-26](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/755fc79a-2a77-402b-aa11-33799e31ee09)
![Screenshot from 2024-03-26 11-39-53](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/45fdc85e-cc32-4b08-954e-bd78dcec0891)
![Screenshot from 2024-03-26 12-00-48](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/5deb6b89-c81e-4b4d-a225-badc1f7c7299)

#### 12. Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![Screenshot from 2024-03-26 12-55-00](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ee26dfa7-715a-4df7-97e7-4c6e54d16522)
![Screenshot from 2024-03-26 12-57-40](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e04a4dfd-000c-406b-bdaa-f5314c4eedef)
![Screenshot from 2024-03-26 12-58-12](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ac27d567-1b72-444d-a638-9be2db677ae2)
![Screenshot from 2024-03-26 13-09-57](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e63cac70-072d-4453-992e-076b94f8f1a2)

#### 13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing `CTS_CLK_BUFFER_LIST`

```tcl
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```

Screenshots of commands run and timing report generated

![Screenshot from 2024-03-26 13-42-03](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2191f13b-ff76-4281-9d3c-52cbf12f9142)
![Screenshot from 2024-03-26 13-45-28](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3dcd6efe-d31a-4f72-aede-be1cdd7b078f)
![Screenshot from 2024-03-26 13-48-01](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2cb2c6fd-1e8c-4921-8553-7dcfb51258e5)
![Screenshot from 2024-03-26 13-48-13](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/70353613-86f2-432c-a1d8-821083e8c209)
![Screenshot from 2024-03-26 13-50-12](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/bf6c116b-e31c-4dce-b04f-a75430b1d03b)
![Screenshot from 2024-03-26 13-53-30](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a26e9d23-d448-4512-8676-8a2b3fb22572)

## Section 5 - Final steps for RTL2GDS using tritonRoute and openSTA (27/07/2025 - 29/07/2025)

### Theory

### Implementation

* Section 5 tasks:-
1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
2. Perfrom detailed routing using TritonRoute.
3. Post-Route parasitic extraction using SPEF extractor.
4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

* All section 5 logs, reports and results can be found in following run folder:

[Section 5 Run - 26-03_08-45](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45)

#### 1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 
```

Screenshots of power distribution network run

![Screenshot from 2024-03-26 14-22-34](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/dd916806-6688-4c96-b1af-156b2d4acfe6)
![Screenshot from 2024-03-26 14-22-46](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/1f6ade75-93c2-4b76-bc46-77d1d532a84c)

Commands to load PDN def in magic in another terminal

```bash
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```

Screenshots of PDN def

![Screenshot from 2024-03-26 14-30-52](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b13997fd-296c-4213-b4f9-8f66a7375e47)
![Screenshot from 2024-03-26 14-32-24](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/79b5f158-acf4-4065-a0ec-61007ab465d0)
![Screenshot from 2024-03-26 14-34-03](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/bee921ce-03d5-49fb-a9fc-bcc6e3402f8c)

#### 2. Perfrom detailed routing using TritonRoute and explore the routed layout.

Command to perform routing

```tcl
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```

Screenshots of routing run

![Screenshot from 2024-03-26 14-48-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/f166be26-f49a-4001-abee-ce395857990f)
![Screenshot from 2024-03-26 15-38-39](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c0c8f372-0293-4fdd-a0a3-691f164e7bed)
![Screenshot from 2024-03-26 15-29-38](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/70a99289-06ea-4eb8-b3b0-4147395c6f9c)

Commands to load routed def in magic in another terminal

```bash
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```

Screenshots of routed def

![Screenshot from 2024-03-26 15-33-12](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6eade230-eb96-4d7b-b7a9-7a7db9c2c8b7)
![Screenshot from 2024-03-26 15-30-36](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b1900c55-7470-41b2-8b4f-3af871494d99)
![Screenshot from 2024-03-26 15-31-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/5faaca5b-fb6e-4abd-946d-6531b35489b8)
![Screenshot from 2024-03-26 15-32-20](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/594ef79b-4755-4934-a087-33fb24996526)

Screenshot of fast route guide present in `openlane/designs/picorv32a/runs/26-03_08-45/tmp/routing` directory

![Screenshot from 2024-03-26 15-41-18](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/1dc38a57-03c9-45c3-acdb-063731a86433)

#### 3. Post-Route parasitic extraction using SPEF extractor.

Commands for SPEF extraction using external tool

```bash
# Change directory
cd Desktop/work/tools/SPEF_EXTRACTOR

# Command extract spef
python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def
```

#### 4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![Screenshot from 2024-03-26 23-16-16](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/72ef3e8d-7ca2-4b60-89ea-de053f9c2902)
![Screenshot from 2024-03-26 23-17-09](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/5cac9ce5-420a-4eaa-b5f4-09286701e550)
![Screenshot from 2024-03-26 23-17-32](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7d809f14-66b6-4dd6-8161-2ad8371cfaf9)
![Screenshot from 2024-03-26 23-17-56](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/64ccb1d8-74aa-42b0-88d4-a0f9588d2ca2)

# Certificate

![Digital-VLSI-SoC-Design-and-Planning-Certificate](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6f292f50-f95b-471c-8dac-bf0ea7345c9b)

# Acknowledgements

* [Kunal Ghosh](https://github.com/kunalg123), Co-founder, VSD Corp. Pvt. Ltd.
* [Nickson P Jose](https://github.com/nickson-jose), Physical Design Engineer, Intel Corporation.
* [R. Timothy Edwards](https://github.com/RTimothyEdwards), Senior Vice President of Analog and Design, efabless Corporation.


