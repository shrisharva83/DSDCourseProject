# DSDCourseProject

The Protocol Conversion Unit (PCU), consists of a Serial In Parallel Out (SIPO) register and an I2C master device. SS line of the SPI master (sender device) is connected to the Enable
 (SS) pin of SIPO. During the transmission of data by the SPI master (sender) a low signal enables SIPO register. SIPO uses clock provided by SPI master on SCLK line. With each clock
 pulse data on the MOSI line of SPI master is shifted into the internal register of SIPO through DIN (serial data in) of SIPO and data initially stored in the internal register of SIPO is shifted out on the MISO line of SPI master through SISO of SIPO. After 8 clock pulses SPI master stops communication and SS line goes low to high. Also SPI master raises a flag
 called DONE. This flag is later used to signal reset of the I2C master. The transition on SS line signals SIPO to load the data in its internal register onto the output bus DOUT. This
 completes the first step in PCU, where the data from sender is received and ready to be sent to the receiver. Address (7 bits) of I2C slave (receiver device) is stored in input address register called AddressI2cMaster (8 bits). R/W bit is appended after the address bits and stored in AddressI2cMaster register. Data on DOUT is loaded into input data register DataI2cMaster
 (8 bits) of I2C master. DONE flag from SPI master sets RESET of I2C master high. This initiates the second step in PCU. Now I2C master initiates its operation. I2C master
 follows the I2C frame format mentioned above. I2C master  stops communication after sending stop bit. At this point data sent by SPI master (sender) is successfully transferred to the
 concerned I2C slave (receiver) and the protocol conversion successfully takes place.

 <img width="481" height="314" alt="image" src="https://github.com/user-attachments/assets/e8f8668f-8033-4288-b2b8-61ab54db0e9c" />
<img width="493" height="210" alt="image" src="https://github.com/user-attachments/assets/fd10c6b3-068e-4093-afa8-a44b42a43be3" />
<img width="392" height="686" alt="image" src="https://github.com/user-attachments/assets/8d80acef-ae62-44f2-a35c-2e0233c427a3" />
<img width="464" height="618" alt="image" src="https://github.com/user-attachments/assets/d3ca3f4f-964c-4766-9900-0ad23b10d8a5" />


