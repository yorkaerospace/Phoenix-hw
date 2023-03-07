# Phoenix

This is the hardware repo for our new RP2040-based flight computer. We aim to use this to provide GPS tracking and parachute deployment on our next generation of rockets.

## Kicad setup
Kicad should be able to view this file perfectly fine without any setup, however if you wish to make changes you'll need to download our [components library](https://github.com/yorkaerospace/YAR-Kicad-Libs/tree/main). You can either download it and drop its contents in the YAR-Kicad-Libs folder, or run:
```bash    
git submodule init
git submodule update
```
## Specs
MCU: [RP2040](https://docs.rs-online.com/f523/A700000007747462.pdf), 2 core ARM M0+ @ 133 MHz  
Storage: 2 x [W25Q128](https://docs.rs-online.com/cdee/0900766b81622f85.pdf) Flash chips, 16MB each.   
Radio: [Si4468/7](https://docs.rs-online.com/cabb/0900766b813b9ac6.pdf)  
GPS: [L70B-M29](https://docs.rs-online.com/74ea/0900766b8147dbe2.pdf)  
Sensors:
- [ADXL 200g](https://docs.rs-online.com/c088/0900766b812d72c4.pdf) Accelerometer
- [I3G4250DTR](https://uk.rs-online.com/web/p/motion-sensor-ics/1116450) Gyroscope
- [MS563702BA03-50](https://uk.rs-online.com/web/p/pressure-sensor-ics/8937168) Barometer

<p align="center">
  <img src="https://github.com/yorkaerospace/Phoenix-hw/blob/main/Phoenix%20Block%20Diagram.drawio.svg" />
</p>

## Known issues (Rev 1)
Revision 1, that was issued to JLCPCB in Jan 2023 has a few issues, in rough order of severity:
- Gyroscope footprint is mirrored. Attempting to fit the gyroscope will cause a short to ground through the gyro.
- Pyro channels are of an unproven design. 
  - Switching on the low side may cause accidental ignition if the ematch were to short to ground.
  - MOSFETS are small for what they need to do.
- GPS footprint has pin 1 marker in the wrong location. Fortunately this is just an issue with the silkscreen, the actual footprint is okay.
- Board is slightly large for some rockets. Would like to reduce size if possible.
- BOM is *huge* making hand-placing components a bit of a headache.
- No-one has mini USB nowadays.


