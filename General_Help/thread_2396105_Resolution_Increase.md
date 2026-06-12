---
title: "Resolution Increase"
date: 2018-07-11
forum: General Help
---

### Post by SpikeLS6 on 2018-07-11
I recently bought a new monitor that is native in 2560 x 1900 resolution, one notch above HD. However, Ubuntu 18.4 only goes to 1920 x 1080. How do I find software to upgrade my display settings?

---

### Post by ajgreeny on 2018-07-11
What hardware, particularly graphic card do you use, with what driver.
Show us the output of ```
lspci -k
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by SpikeLS6 on 2018-07-11
I have an LG 34WK650-W monitor using an AMD Radeon RX560 4G/128 bit video card.

```
mckenzie@mckenzie-desktop:~$ lspci -k
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge (rev 02)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
    Subsystem: ASUSTeK Computer Inc. SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Kernel driver in use: ohci-pci
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Kernel driver in use: ohci-pci
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. SBx00 Azalia (Intel HDA)
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Kernel driver in use: ohci-pci
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Kernel driver in use: ohci-pci
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Polaris11] (rev cf)
    Subsystem: Gigabyte Technology Co., Ltd Baffin [Radeon RX 560]
    Kernel modules: amdgpu
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0
    Subsystem: Gigabyte Technology Co., Ltd Device aae0
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8 series motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
    Subsystem: ASUSTeK Computer Inc. P8B WS Motherboard
    Kernel driver in use: xhci_hcd
mckenzie@mckenzie-desktop:~$
```

---

### Post by friedchips2 on 2018-07-11
[https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

see xorg configuration section of that page. You will need to specify your resolution in the config if EDID is not properly setting it.

---

### Post by friedchips2 on 2018-07-11
Post the output of

xrandr

---

### Post by SpikeLS6 on 2018-07-12
xrandr output

mckenzie@mckenzie-desktop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080      0.00* 
   1280x1024      0.00  
   1024x768       0.00  
   800x600        0.00  
   640x480        0.00  
mckenzie@mckenzie-desktop:~$

---

### Post by mIk3_08 on 2018-07-12
Does the resolution output of your machine does not depends on the capability of your video card? "AMD Radeon RX560 4G/128" I got it... sorry.

---

### Post by mIk3_08 on 2018-07-12
> **SpikeLS6 said:**
> I have an LG 34WK650-W monitor using an AMD Radeon RX560 4G/128 bit video card.

```
mckenzie@mckenzie-desktop:~$ lspci -k
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge (rev 02)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
    Subsystem: ASUSTeK Computer Inc. SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Kernel driver in use: ohci-pci
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Kernel driver in use: ohci-pci
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. SBx00 Azalia (Intel HDA)
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Kernel driver in use: ohci-pci
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Kernel driver in use: ohci-pci
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Kernel driver in use: ehci-pci
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Polaris11] (rev cf)
    Subsystem: Gigabyte Technology Co., Ltd Baffin [Radeon RX 560]
    Kernel modules: amdgpu
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0
    Subsystem: Gigabyte Technology Co., Ltd Device aae0
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8 series motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
    Subsystem: ASUSTeK Computer Inc. P8B WS Motherboard
    Kernel driver in use: xhci_hcd
mckenzie@mckenzie-desktop:~$
```



SpikeLS6 can you post your machine hardware specification including the Ubuntu O.S specification.

---

### Post by SpikeLS6 on 2018-07-12
Not sure what you mean by "machine hardware specification including the Ubuntu O.S specification. 				" The RX560 is capable for 5120 x 2880 resolution, more than enough for the LG 34WK650-W monitor. Professional computer shop installation.

---

### Post by mIk3_08 on 2018-07-12
I mean PC hardware specification...

---

### Post by SpikeLS6 on 2018-07-12
AMD Quad-Core FX(tm)-6300 Six-Core Processor, speed 3.5,  with 8 Gig RAM.

---

### Post by NM5TF on 2018-07-12
can you post the output of

```
inxi -G
```

you might have to install inxi first...

this will tell us which driver it is using.....

you might find some help here:

[https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux]("https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux")

tommy

---

### Post by mIk3_08 on 2018-07-12
SpikeLS6, Are you the one who build your own (system machine) PC? How about your O.S specification.

---

### Post by NM5TF on 2018-07-13
> **mIk3_08 said:**
> SpikeLS6, Are you the one who build your own (system machine) PC? How about your O.S specification.

in his original post he says he is using Ubuntu 18.04...;)

---

### Post by mIk3_08 on 2018-07-13
> **NM5TF said:**
> in his original post he says he is using Ubuntu 18.04...;)


Just want to know if he is using desktop, Server, and 32bit or 64bit OS.

---

### Post by SpikeLS6 on 2018-07-13
I upgraded to Ubuntu 18.4  through The usual automatic update advisories that come in, so it should have come from the regular Ubuntu servers. This PC is a Desktop and I believe Ubuntu is loading as a 64-bit system.

---

### Post by SpikeLS6 on 2018-07-13
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Baffin [Polaris11]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
           Resolution: 1920x1080@0.00hz
           OpenGL: renderer: llvmpipe (LLVM 5.0, 128 bits)
           version: 3.3 Mesa 17.3.3
mckenzie@mckenzie-desktop:~$ 

I need to get to 2560 x 1080 or greater.

---

### Post by NM5TF on 2018-07-13
latest version of X.org is 1.20....you have 1.19.6

your resolution of 1920x1080@0.00Hz seems incorrect.....are you sure it isn't @60.00Hz ???

I provided you with a link earlier, did you check it out ???

[https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux]("https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux")

---

### Post by SpikeLS6 on 2018-07-13
Found the updated drive for Ubuntu 18.4 on the AMD download page. I downloaded and extracted it to file /home/downloads/AMDGPU-PRO-18.10-572953. Now I can not get to that file with a cd command. I am missing quite a bit of basic Ubuntu Terminal.

what are the commands to install it?

By the way, I questioned the 00hz refresh rate, too. Going through the video card specs I think it ought to be 60hz, but have no idea how to change it. Hopefully that will be included in the driver update.

---

### Post by mIk3_08 on 2018-07-13
some ATI may require the proprietary fglrx driver.

Try to read this one maybe it will help. [Click here.]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD")

---

### Post by mIk3_08 on 2018-07-13
> **SpikeLS6 said:**
> Found the updated drive for Ubuntu 18.4 on the AMD download page. I downloaded and extracted it to file /home/downloads/AMDGPU-PRO-18.10-572953. Now I can not get to that file with a cd command. I am missing quite a bit of basic Ubuntu Terminal.

what are the commands to install it?

By the way, I questioned the 00hz refresh rate, too. Going through the video card specs I think it ought to be 60hz, but have no idea how to change it. Hopefully that will be included in the driver update.



Hi SpikeLS6 Custom Screen Resolution in Ubuntu Desktop.
This may take some risk but you can try this one for a custom display resolution just [ Click Here]("http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/").

---

### Post by SpikeLS6 on 2018-07-14
Found & downloaded the AMDGPU-PRO-18.10-572953, extracted it, then installed it. It went through the installation successfully and I did the recommended reboot. However, during the reboot it stopped on "Started Update UTMP about System Runlevel Changes" and locked up right there. After 20 minutes, I pressed the Reset button to force a reboot, but no matter if I use the regular Kernel or the Recovery Kernel the reboot stops in the same place. 18.04 simply will not boot up.

Anything I  can do from here to get back to normal?

---

### Post by mIk3_08 on 2018-07-14
"Found & downloaded the AMDGPU-PRO-18.10-572953" Can you give some link where you downloaded the software, so we can check the said software.

---

### Post by SpikeLS6 on 2018-07-14
[https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx)

Scoll down and I used "Radeon Software for Linux Version 18.20 for Ubuntu 18.04.

---

### Post by mIk3_08 on 2018-07-14
try to use Ctrl+Alt F2

---

### Post by SpikeLS6 on 2018-07-14
Ctrl + Alt + F2 got me into Terminal and asked me for user name and password. I input them and when the prompt came up again input Reboot. It did and I brought it back up into Recovery mode, but eventually came up with the same "Started Update UTMP about System Runlevel Changes".

Ctrl + Alt + F2 got me back to the Terminal Log in where it sits now.

---

### Post by mIk3_08 on 2018-07-14
Try this link [Click here]("https://unix.stackexchange.com/questions/451348/ubuntu-boot-hangs-at-started-update-utmp-about-system-boot-shutdown")

For diagnosing boot problems [And here]("https://freedesktop.org/wiki/Software/systemd/Debugging/#index1h1")

---

### Post by mIk3_08 on 2018-07-14
Here some video maybe it can help; [click here]("https://www.youtube.com/watch?v=kM__yadgbek")

---

### Post by SpikeLS6 on 2018-07-14
I tried the "journalctl" command and got thousands of lines of information, but no way of knowing what they mean.

Then I tried "journalctl -b" which gave me today's date and thousands of lines of information. One thing that stuct out on  this one was an "error opening ATTR{/sys/dev" printed in RED font.

I am sorry I do not know more I can tell you on this one.

---

### Post by SpikeLS6 on 2018-07-14
Getting no where with this problem and have spent the day Googling Ubuntu information about it. Am I at the point of having to completely reformatting the SSD, then doing a fresh install of 18.04? I know I will have to load all the programs and backed up files, but if that is the solution I may need to get started to get the PC back into service. Thanks.

---

### Post by friedchips2 on 2018-07-14
Did you make seperate /home partition when you installed?

---

### Post by mIk3_08 on 2018-07-14
> **SpikeLS6 said:**
> Getting no where with this problem and have spent the day Googling Ubuntu information about it. Am I at the point of having to completely reformatting the SSD, then doing a fresh install of 18.04? I know I will have to load all the programs and backed up files, but if that is the solution I may need to get started to get the PC back into service. Thanks.


If you decide to reformat your ssd and install new Ubuntu you can do it on your own. 
Here some links that will guide you thru.

Download Ubuntu links [Click Here]("https://www.ubuntu.com/download")
Alternatives [Click Here]("https://www.ubuntu.com/download/alternative-downloads")

Methods to install using USB [Click Here]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.131301702.876384817.1531028389-1135655536.1531028389#0") 
Other Methods [Click Here]("https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.228586648.449881734.1531449427-729107667.1531449427#0")

But if you decide to go to service that is more convenient.

---

### Post by SpikeLS6 on 2018-07-15
This was a fairly new PC, but I converted the HDD to SDD and had the shop set up one for WIN 10 and the other for Ubuntu. It worked so I did not delved into it any more.

Standby, I am getting busy the rest of the week, but want to redo 18.04, I need to get the PC operable again. Thank everyone for all your help. I'll let  you know how  this redo comes out.

---

### Post by mIk3_08 on 2018-07-15
okay, Best of luck SpikeLS6.

---

