---
title: "Brightness Problem"
date: 2013-06-06
forum: General Help
---

### Post by bidyut100 on 2013-06-06
Dell Vostro Laptop brightness is zero. After reinstall ubuntu 12.04 also, brightness not increased.
Pls. help how to increase brightness.

---

### Post by Toz on 2013-06-06
Hello and welcome to the forums.

Can you provide some more information?

1. What model of Vostro do you have?

2. What video card(s) and drivers are you using? From a terminal window, type in the following command and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

3. Are you using any kernel boot parameters:
```
cat /proc/cmdline
```
...if not, you may want to try **acpi_backlight=vendor**. See the Kernel Boot Parameters link in my signature for more information on how to do this.

4. What backlight interfaces do you have?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by greatsirkain on 2013-06-06
Also check simple stuff like the shortcut keys on your laptop, eg on mine fn+f9 turns the brightness up.
Had to 'fix' a friends laptop the other day because he said the ubuntu install I put on wouldn't connect to the internet, turned out he'd rolled on it in his sleep and pressed fn+f key and switched wireless off :P
After a google of your laptop the brightness keys are fn+f5 & fn+f4, a lot of people seem to be having this problem after an OS change. Other suggestions for a fix I read were to check you have the Nvidia A07 video drivers or to update your BIOS

---

### Post by bidyut100 on 2013-06-08
My laptop name DELL Vostro A860, The details of Laptop:
```
                         TR320
                                       1
                                    SERVICE CHARGE..., DRIVER..., WIRELESS..., 1395, REST OF WORLD...
             
                                             F286H
                                       1
                                    Battery, Primary, 48WHR, 6C      Lithium, SIMPLO
             
                                             J075D
                                       1
                                    Processor, T2390, 1.86, 1MB, 2C   Pentium Merom Dual Core, M0
             
                                             P065X
                                       1
                                    Card, Wireless, Network, Atheros Component Engineering, Taipei  101/shanghai World
             
                                             P927C
                                       1
                                    Assembly, Inverter, Liquid      Crystal Display, Cold Cathode  Fluorescent Lamp, H/P
             
                                             R811H
                                       1
                                    Keyboard, 86, United States     English, Single Pointing       A840/A860
             
                                             RX399
                                       1
                                    Card, Wireless, Internal        Bluetooth, DW360, Windows Vista Os
             
                                             XN072
                                       1
                                    DVD+/-RW..., 8X, Serial ATA..., SMALL FORM FACTOR..., TOSHIBA SAMSUNG STORAGE TECHNOLOGY...
             
                                             H417H
                                       1
                                    BASE (ASSEMBLY OR GROUP)..., NOTEBOOK..., PMER, T2390, A860, INB4
             
                                             J986H
                                       1
                                    Assembly, Cable, Low Voltage    Differential Signaling, Liquid Crystal Display, 15.6, A860
             
                                             J996H
                                       1
                                    Assembly, Cover, Hinge, A860
             
                                             J998H
                                       1
                                    Assembly, Palmrest, A860
             
                                             K390J
                                       1
                                    Cover, Liquid Crystal Display  15.6, Black, Vostro Notebook    A860
             
                                             M094G
                                       1
                                    LIQUID CRYSTAL DISPLAY..., 15.6, HIGH DEFINITION..., 1CCFL, ANTI GLARE..., AU OPTRONICS CORP...
             
                                             M702H
                                       1
                                    Heatsink, Central Processor    Unit, Notebook, A840/A860
             
                                             M703H
                                       1
                                    Fan, 60X46X11MM, Central        Processor Unit, A840/A860
             
                                             M858H
                                       1
                                    Bezel, Liquid Crystal Display  15.6, A860
             
                                             Y487G
                                       1
                                    ASSEMBLY..., BASE (ASSEMBLY OR GROUP)..., NOTEBOOK..., DEVICE..., A860
             
                                             YD637
                                       1
                                    Assembly, Adapter, ALTERNATING CURRENT..., 65W, M07   LTON, 3 Pin
             
                                             M712H
                                       1
                                    Assembly, Printed Wiring Assy  Planar, Unified Memory         Architecture, A860
             
                                             P254X
                                       1
                                    ASSEMBLY..., BASE (ASSEMBLY OR GROUP)..., NOTEBOOK..., T2390, INB4, A860
             
                                             J692J
                                       1
                                    HARD DRIVE..., 120GB, S2, 5.4K, 2.5, WD-ML160
             
                                             57154
                                       1
                                    Service Charge, Software, Windows 98, Fully Integrated   System Test
             
                                             57154
                                       1
                                    Service Charge, Software, Windows 98, Fully Integrated   System Test
             
                                             58548
                                       1
                                    INFORMATION..., SOFTWARE..., STUFF, 10MB
             
                                             58548
                                       1
                                    INFORMATION..., SOFTWARE..., STUFF, 10MB
             
                                             8564U
                                       1
                                    INFORMATION..., SOFTWARE..., DEFAULT, NEW TECHNOLOGY FILE SYSTEM...
             
                                             9472R
                                       1
                                    Information, Software, Linux-   Partition
             
                                             3K644
                                       1
                                    Information, Storage Processor APIC-CONTROLLER
             
                                             2K158
                                       1
                                    INFORMATION..., COUNTRY, INDIA, ASIA PACIFIC CUSTOMER CENTER...
             
                                             X7745
                                       1
                                    Service Charge, Software, DKMS  Utilities, Utility, Operating  System, Red Hat Enterprise     Linux, Precision Workstation
             
                                             D7952
                                       1
                                    INFORMATION..., WXPSP2, DISABLE XD
             
                                             T1945
                                       1
                                    INFORMATION..., FORCE, 32BIT, PROCESS-ON
             
                                             HG095
                                       1
                                    Service Charge, Software       On Board Diagnostics, Notebook
             
                                             PJ289
                                       1
                                    INFORMATION..., VPEPR
             
                                             XT321
                                       1
                                    SERVICE CHARGE..., SOFTWARE..., WINDOWS XP..., VOS NBK, WALLPAPER...
             
                                             K128F
                                       1
                                    SERVICE CHARGE..., SOFTWARE..., CLIENT..., UBUNTU8.04
             
                                             P191X
                                       1
                                    SERVICE CHARGE..., SOFTWARE..., INITIAL RAM DISK..., UBUNTU, VOS
             
                                             P638H
                                       1
                                    INFORMATION..., BTS
             
                                             CU458
                                       1
                                    Information, Direct Ship       Quanta, 1501
             
                                             J822H
                                       1
                                    SERVICE CHARGE..., DRIVER..., MODEM DAUGHTER CARD..., CONEXANT SYSTEMS INC...., A860
             
                                             P578H
                                       1
                                    SERVICE CHARGE..., DRIVER..., BLUETOOTH..., USI, A860
             
                                             Y482G
                                       1
                                    SERVICE CHARGE..., DRIVER..., AUDIO..., VOS NBK, A860
             
                                             Y490G
                                       1
                                    SERVICE CHARGE..., DRIVER..., WIRELESS..., QMI, EM112, A860
             
                                             Y492G
                                       1
                                    SERVICE CHARGE..., DRIVER..., TOUCHPAD..., VOS NBK, A860
             
                                             Y496G
                                       1
                                    SERVICE CHARGE..., DRIVER..., CHIP SET..., INTEL..., VOS NBK, A860
             
                                             Y500G
                                       1
                                    SERVICE CHARGE..., DRIVER..., VIDEO..., VOS NKB, A860
             
                                             Y503G
                                       1
                                    SERVICE CHARGE..., DRIVER..., CARD READER..., VOS NBK, A860
             
                                             Y506G
                                       1
                                    SERVICE CHARGE..., SOFTWARE..., POWER..., MANAGEMENT..., UTILITY, A860
             
                                             Y511G
                                       1
                                    SERVICE CHARGE..., DRIVER..., LAN ON MOTHERBOARD..., VOS NBK, A860
```
Pls. help.
I am not able to see the laptop screen properly, that why I am unable to give the details, after running the programme.
Suggest how to uninstall it again reinstall windows xp. 
Thanking you all.

---

### Post by Toz on 2013-06-08
> **bidyut100 said:**
> 
Pls. help.
I am not able to see the laptop screen properly, that why I am unable to give the details, after running the programme.
Follow the _"Temporarily Add A Kernel Boot Parameter for Testing"_ instructions from [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") and add the parameters **acpi_osi=Linux acpi_backlight=vendor** after the existing "quiet splash" entry to see if that helps with the screen brightness.
> Suggest how to uninstall it again reinstall windows xp. 
Thanking you all.
If you wish to reinstall Windows XP, simply boot from the Windows XP CD and follow the instructions.

---

### Post by firekage on 2013-06-08
You mean by fn keys? Add to grub in cmd line, where is "quiet splash" this line: acapi_backlight=vendor and update grub.

---

