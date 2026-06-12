---
title: "Upgrade 13.10 to 14.04 broke graphics and UI"
date: 2014-04-30
forum: General Help
---

### Post by texpat on 2014-04-30
The whole process ran smoothly up to reboot. My graphics are borked and I don't get a user interface beyond the login screen.

13.10 ran well with a dual screen setup which I configured via the nvidia driver's interface. Now I get output only to one screen (that was expected) and resolution is very low (looks like some fallback setting).

I suppose that could be solved by tweaking the display settings, but the problem is I don't get a user interface once I log in. No reaction from mouse clicking or from key pressing.

What can I do to get this sorted out?

Thanks for reading and for any pointers.
Tx

---

### Post by kc1di on 2014-04-30
Try booting with nomodeset  when ubuntu starts to boot hold down left shift key then select f6 from the menu select nomodeset and hit esc then enter. see if you can get into the gui, your resolution will be bad. but if you get in then reinstall your video drivers and reboot. good luck.

---

### Post by texpat on 2014-04-30
Pressing the left shift key produces the gru menu. No f6 to be selected appears...

I tried also: advanced ubuntu options > recovery mode > failsafeX. This runs fsck and then hangs...

---

### Post by kc1di on 2014-04-30
make sure you press the left shift key just as it's begining to boot.  you should see a page the has a list of function key entries at the bottom of the page ,F6 being the one on the far left.  it say other or something like that, under it's menu nomodeset is the last entry.

---

### Post by texpat on 2014-04-30
Been trying now for the last hour or so. Seems to require millisecond-precise timing... its just not happening.

I can get a text console with CTRL+ALT+F1. Can I try reinstalling drivers from there?

---

### Post by kc1di on 2014-04-30
you can try but I don't know which one you'll need. if you get to the terminal type:
```
lspci
``` and list the results here.  
If you already know the name of the driver you can try to install it. 
Here are the options available via the Ubuntu repositories:
```
 nvidia-173
nvidia-304
nividia-310
nividia-313
nvidia-319
nvidia-331
```

to install one of them you would do this ```
 sudo apt-get update
sudo apt-get install nvidia-<then the number of the driver that's right for your card> 
```
For my nvidia card it's 304 so for my machine it would look like this ```
 sudo apt-get install nvidia-304
```
good luck

---

### Post by texpat on 2014-04-30
Result of lspci

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460 SE] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF104 High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```

---

### Post by kc1di on 2014-04-30
That's a pretty old Video card for this release.  It's a Nvidia GeForce GTX 460 SE. 
Try the the 304 driver.  it's supposed to handle most legacy cards. 
so use this command ```
sudo apt-get install nvidia-304
```
No guarantees though.
According to Nvidia your card is supposed to be support by this driver.
[See here.]("http://www.nvidia.com/object/linux-display-ia32-304.37-driver")

---

### Post by texpat on 2014-05-02
So, I tried this and some other stuff I found. Basically all the same, though: manually install the nvidia drivers.

It worked mostly in that the drivers were installed. But it didn't bring back unity, so that doesn't seem to be the problem.

Anyway, I backed up the stuff I needed (rsynced from the text console) and did a clean reinstall; with Xubuntu this time - snappier than unity on my ageing hardware. Bit of a pain having to rebuild from scratch, but I'm back in the saddle again :-)

Sorry I decided to cop out, but I needed the machine back up and working again asap.

Thanks for your efforts to help out.

---

