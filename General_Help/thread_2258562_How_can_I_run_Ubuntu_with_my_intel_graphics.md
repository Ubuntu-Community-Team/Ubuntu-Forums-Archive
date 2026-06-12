---
title: "How can I run Ubuntu with my intel graphics?"
date: 2014-12-28
forum: General Help
---

### Post by petermartin2 on 2014-12-28
I have huge troubles with my videocard Radeon 7770, I have tried the open source drivers as well as proprietary drivers, I have reinstalled the system 6 times. The errors are different sometime the whole OS crashes and I have to restart sometimes I'm taken to a terminal but it's black and it says that the graphics are not proparly installed sometimesit freezes at startup and with one of the drivers it just went completely black so I had to delete everything from windows. Nothing works so I got the suggestion to try running it from Intel Graphics, but how do I do this? Do I need to do anything else than install the intel driver? I don't have bios on my mothercard it would seem that's not an option that comes on at startup.

Very grateful for any help as this is really making the OS impossible to use properly

---

### Post by buzzingrobot on 2014-12-28
You don't need to install an Intel video driver.  It's incorporated in the kernel. If you switch the machine from the Radeon to Intel video and reboot, you will be using the Intel driver.

Every PC has a BIOS, or its newer equivalent, UEFI. It initializes the hardware and passes control to the operating system.  Check your machine's manual (your copy or online) to determine the keystroke needed during the boot process to activate the BIOS/UEFI settings menu.  (While I imagine it is theoretically possible for a vendor to fail to include a BIOS/UEFI settings menu, I've never heard of it.)

---

### Post by petermartin2 on 2014-12-28
> **buzzingrobot said:**
> You don't need to install an Intel video driver.  It's incorporated in the kernel. If you switch the machine from the Radeon to Intel video and reboot, you will be using the Intel driver.

Every PC has a BIOS, or its newer equivalent, UEFI. It initializes the hardware and passes control to the operating system.  Check your machine's manual (your copy or online) to determine the keystroke needed during the boot process to activate the BIOS/UEFI settings menu.  (While I imagine it is theoretically possible for a vendor to fail to include a BIOS/UEFI settings menu, I've never heard of it.)

I will try and find a manual for my motherboard online. I have already looked through the UEFI but I haven't found change video settings or anything like it. Do you have any suggestions what to look for?

---

### Post by buzzingrobot on 2014-12-28
> **petermartin2 said:**
> I will try and find a manual for my motherboard online. I have already looked through the UEFI but I haven't found change video settings or anything like it. Do you have any suggestions what to look for?

In mine, 'Video' is a sub-entry under 'Devices'.

If you are accessing your UEFI settings menu, what keystroke are you using and what do you see when the menu displays?

---

### Post by petermartin2 on 2014-12-29
> **buzzingrobot said:**
> In mine, 'Video' is a sub-entry under 'Devices'.

If you are accessing your UEFI settings menu, what keystroke are you using and what do you see when the menu displays?

Keystroke is F2 for UEFI. My UEFI don't have devices, options are as follows:

[ http://oi59.tinypic.com/2uorknq.jpg]("http://oi59.tinypic.com/2uorknq.jpg")
UEFI Version: Z77E-ITX P1.30
Processor Type: Intel (R) Core (TM) i7-3770K CPU @ 3.50GHz
Processor Speed: 3500MHz
Microcode Update: 306A9/12
Cache Size: 8192KB
Total Memory: 16384MB, Dual-Channel Memory Mode
DDR3_A1: 8192MB (DDR3-1600)
DDR3_B1: 8192MB (DDR3-1600)

[ http://oi59.tinypic.com/rrjdyo.jpg]("http://oi59.tinypic.com/rrjdyo.jpg")
Load Optimized GPU OC Setting
CPU CONFIGURATION
CPU Ratio
Host Clock Override (BCLK)
Spread Spectrum
Intel SpeedStep Technology
Intel Turbo Boost Technology
Additional Turbo Voltage
Internal PLL Overvoltage
Long Duration Power Limit
Long Duration Maintained
Short Duration Power Limit
Primary Plane Current Limit
Secondary Plane Current Limit
GT OverClocking Support

[ http://oi58.tinypic.com/14jvv2c.jpg]("http://oi58.tinypic.com/14jvv2c.jpg")
GT OverClocking Support
Dram Timing Configuration
XMP 1.3 Profile 1: DDR3-1600 10-10-10-27 1.50V
Load XMP Setting
Dram Frequency  DDr3-1600
DRAM Configuration
Power Saving Mode CPU Voltage
CPU Load-Line Calibration Level 5
IGPU Voltage
IGPU Load-Line Calibration Level 5
DRAM Voltage 1.500V
VTT Voltage 1.053V

[IMG]http://oi58.tinypic.com/xc95og.jpg[/IMG]
CPU Configuration
North Bridge Configuration
South Bridge Configuration
Storage Configuration
Intel(R) Rapid Start Technology
Intel(R) Smart Connect Technology
Super IO Configuration
ACPI Configuration
USB Configuration
Network Configuration
UEFI UPDATE UTILITY
Instant Flash
Internet Flash - DHCP (AUTO IP), Europe

[IMG]http://oi57.tinypic.com/29dhb7p.jpg[/IMG]
CPU Temparute      : 47.5 *C
M/B Temperature    : 36.0 *C
CPU Fan 1 Speed    : 19852 RPM
Chassis Fan 1 Speed: 588 RPM

Vcore                        :+1.024 V
+5.00V                      :+5.064 V
+12.00V                     :+12.196 V
+3.30V                      :+3.360 V

CPU Fan 1 Setting           Automatic mode
Target CPU Temperature      45 *C/113 *F
Target Fan Speed            Level 3
Chassis Fan 1 Setting       Automatic Mode
Target CPU Temperature     45 *C/113 *F
Target Fan Speed           Level 3
Dehumidifier Function       Disabled

[IMG]http://oi62.tinypic.com/30x8wa0.jpg[/IMG]
Boot Option Priorities
Boot Option #1
Boot Option #2
Hard Drive BBS priporities
CD/DVD ROM DRive BBS Priorities
Setup Prompt Timeout                 1
Bootup Num-Lock
PCI ROM Priority         Enabled
Full Screen Logo         Enabled 
AddOn ROM Display
Boot Failue Guard          Enabled
Boot Failure Guard Count     3
Boot From Onoard Lan         Disabled

[IMG]http://oi60.tinypic.com/6h3hpx.jpg[/IMG]
Boot Option Priorities
Boot Option #1
Boot Option #2
Hard Drive BBS priporities
CD/DVD ROM DRive BBS Priorities
Setup Prompt Timeout                 1
Bootup Num-Lock
PCI ROM Priority         Enabled
Full Screen Logo         Enabled 
AddOn ROM Display
Boot Failue Guard          Enabled
Boot Failure Guard Count     3
Boot From Onoard Lan         Disabled

 [IMG]http://oi60.tinypic.com/6h3hpx.jpg[/IMG]
Security
Sopervisor Passwod
User Password
Supervisor Passwdord
User Password

[IMG]http://oi60.tinypic.com/rie0i8.jpg[/IMG]
Save changes and Exit
Discard Changes  and Exit
Discard Changes and Exit
 Discard Changes 
Load UEFI Defaults
Launch EFI shell from filesystemdevice



I found the manual to my Z77E-ITX card and the only thing I could find that seemed to have something to do with this was "Change primary graphics adapter" hidden away under advanced -> Advanced\North Bridge Configuration

I changed this from PCI Express:
[IMG]http://oi60.tinypic.com/24oayqt.jpg[/IMG]

To "Onboard":

[IMG]http://oi62.tinypic.com/2ytxz46.jpg[/IMG]

However rebooting with these settings resulted in the computer not showing boot menu or mothercard display for 3 straight boots in which Ubuntu performed even worse than before the launcher was gone and I could basically do nothing. On the fourth reboot the computer died completely and would not enter any OS or any kind of boot menu, motherboard or ubuntu boot menu and this wasn't solved until I reset the motherboard. Now I am back with crashing browsers and textinput gone wild..

I'm thinking of trying another graphics card instead..

---

### Post by petermartin2 on 2014-12-29
I disregarded the VT-D capability because it says "unsupported"? But it is the only other thing I can think of that could be the intel graphics. That is strange because my CPU and motherboard both support intel graphics:
[http://www.asrock.com/mb/Intel/z77e-itx/](http://www.asrock.com/mb/Intel/z77e-itx/)
[http://ark.intel.com/products/65523](http://ark.intel.com/products/65523)

---

### Post by buzzingrobot on 2014-12-29
> **petermartin2 said:**
> 
I found the manual to my Z77E-ITX card and the only thing I could find that seemed to have something to do with this was "Change primary graphics adapter" hidden away under advanced -> Advanced\North Bridge Configuration

to "Onboard":
However rebooting with these settings resulted in the computer not showing boot menu or mothercard display for 3 straight boots in which Ubuntu performed even worse than before the launcher was gone and I could basically do nothing. On the fourth reboot the computer died completely and would not enter any OS or any kind of boot menu, motherboard or ubuntu boot menu and this wasn't solved until I reset the motherboard. Now I am back with crashing browsers and textinput gone wild..



The specs for that board include onboard Intel video, so you've switched it correctly. The Intel will use a different port than the Radeon so you need to be sure you've used the correct cable to connect the display to that port, and then set the display to use it, as well.  Otherwise, the display gets no signal.

---

### Post by petermartin2 on 2014-12-29
> **buzzingrobot said:**
> The specs for that board include onboard Intel video, so you've switched it correctly. The Intel will use a different port than the Radeon so you need to be sure you've used the correct cable to connect the display to that port, and then set the display to use it, as well.  Otherwise, the display gets no signal.

Ok I'm going to take the computer apart and look at it and post more photos

---

### Post by petermartin2 on 2014-12-29
Ok I managed to change the uefi according to your suggestions but OS still very buggy getting a lot of system error messages after turning on apport, and compiz and login screen buggy still. I guess this might be because of crashes that occured while running on the radeon so I should probably trying reinstall. Only sad thing about this is that it will probably be hard to switch back and forth between the radeon and the intel graphics. I would really like to use the radeon for windows and gaming but I guess it's all or nothing? Or maybe I could just try and really remember never loging onto Ubuntu from with the video card enabled in UEFI but that would be risky as it might crash Ubuntu again if I forget..

Anyway going to reinstall once more now, thank you so much for your assistance!

---

### Post by grahammechanical on 2014-12-29
Have you read this?

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards

---

### Post by petermartin2 on 2014-12-29
> **grahammechanical said:**
> Have you read this?

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards


[LIST]
[*]fglrx or fglrx-updates 
[/LIST]
these I've installed over and over again they don't work and have very low rating in the software center.

I tried updating my system instead but the updater bugged out so I think I simply have to reinstall everything one more time and hope that it will work running on the intel graphics only

---

### Post by buzzingrobot on 2014-12-29
> **petermartin2 said:**
> 
[LIST]
[*]fglrx or fglrx-updates 
[/LIST]
these I've installed over and over again they don't work and have very low rating in the software center.

I tried updating my system instead but the updater bugged out so I think I simply have to reinstall everything one more time and hope that it will work running on the intel graphics only

Proprietary drivers need to be cleanly removed before installing a different version of the same drivers.  The "Additional Drivers" function in Ubuntu handles that well.  It's common to have problems if they've been installed another way.

The kernel will detect the hardware in use as it boots.  So, if the machine is on the Radeon, the open-source Radeon driver will be used (arguably, it's competitive these days with fglrx in many respects).  If the machine is on the Intel, that will be used. 

If there's an issue with the Intel, you should see it during the boot and use of the live image, before the install.

---

### Post by petermartin2 on 2014-12-29
> **buzzingrobot said:**
> 
If there's an issue with the Intel, you should see it during the boot and use of the live image, before the install.

I have now been working with the ubuntu install on intel graphics today and it has not crashed so far. Also no programs has crashed. only login screen still dosen't work when I tweak it with ubuntu tweak but not all of the problems must have been with the graphic card I guess so I'm going to try and look for other solutions to that. Feels pretty stable now, I hope I won't have to install it again for a while!

---

