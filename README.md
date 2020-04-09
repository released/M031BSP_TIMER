# M031BSP_TIMER
 M031BSP_TIMER

update @ 2020/04/09

1. use M031 EVM , with LED GPIO (PB14) , toggle with 1000ms , capture with scope

with TMR1SEL_HIRC
![image](https://github.com/released/M031BSP_TIMER/blob/master/TMR1SEL_HIRC.jpg)

with TMR1SEL_PCLK0
![image](https://github.com/released/M031BSP_TIMER/blob/master/TMR1SEL_PCLK0.jpg)

2. How to get checksum under KEILC

- get srecord from http://srecord.sourceforge.net/

- put srec_cat.exe under project
![image](https://github.com/released/M031BSP_TIMER/blob/master/srec_under%20project.png)


- add srecord command line into post build

.\obj\srec_cat .\obj\@L.hex -intel -Checksum_Positive_Big_Endian 0x20000 4 -o -HEX_Dump

![image](https://github.com/released/M031BSP_TIMER/blob/master/srec_add%20to%20post%20build.png)

![image](https://github.com/released/M031BSP_TIMER/blob/master/srec_add%20to%20post%20build%20result.png)

- or under same folder with srec_cat.exe, create bat file as below

**************

;srec_cat template.hex -intel -Checksum_Positive_Big_Endian 0x20000 4 -crop 0x20000 0x20004 -o -HEX_Dump

srec_cat template.hex -intel -Checksum_Positive_Big_Endian 0x20000 4 -o -HEX_Dump

pause

**************

- after build project , create hex file , execute the bat file in File manager
![image](https://github.com/released/M031BSP_TIMER/blob/master/srec_under%20project%20with%20bat.png)


3. explanation

- 0x20000 : MCU max flash size range

- template.hex : project file name in KEILC

- 0x20000 4 : at this address after 4 bytes, display check sum

