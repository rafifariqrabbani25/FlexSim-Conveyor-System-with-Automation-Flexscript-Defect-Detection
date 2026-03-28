A discrete-event simulation model built in FlexSim that simulates a manufacturing conveyor line with automated item classification, defect detection, and multi-destination routing.

![Model Image](<Screenshot 2026-03-29 003543.png>)

https://github.com/rafifariqrabbani25/FlexSim-Conveyor-System-with-Automation-Flexscript-Defect-Detection/raw/main/Flexim%20Model.mp4

## 1. How It Works
- Item Generation (Source1): creates items at a defined interarrival time
- Label Assignment: each item is assigned two attributes:
1. Type: randomly assigned 1, 2, 3, or 4 using duniform(1,4,...)
2. Defect: 30% chance of being defective using bernoulli(30,1,0,...)
3. Color Coding: items are colored based on Type; defective items turn black
4. Detection: a Station holds the item briefly for inspection; a Photo Eye scans each item and repairs defective items by resetting their Defect value to 0
5. Routing: at the decision point, items are routed based on Type + Defect combination, implemented via FlexScript on the conveyor's onContinue trigger:
6. Processing: defective items (that were not repaired) proceed to Processor1

## 2. Key Components
- Source1: Generates items with random Type & Defect attributes
- Conveyor: Transports items along U-shaped track
- Station: Holds item for a set process time during inspection
- Photo Eye: Scans each item and converts defective items to non-defective (repair)
- Operator1: Assists during the inspection process at the Station
- Queue1: Receives normal Type 1 items
- Queue2: Receives normal Type 2 items
- Queue3: Receives normal Type 3 and 4 items
- Processor1: Processes defective items
