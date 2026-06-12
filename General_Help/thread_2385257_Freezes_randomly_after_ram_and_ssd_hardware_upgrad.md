---
title: "Freezes randomly after ram and ssd hardware upgrade"
date: 2018-02-18
forum: General Help
---

### Post by pedrovgp on 2018-02-18
I have used Ubuntu 16.04 for quite a while now.
My laptop hag 4GB RAM and a 750GB HD. I have upgraded it adding extra 8GB RAM (totalling 12GB RAM) and replacing the HD with a 256GB SSD.

After upgrading, I made a fresh install of Ubuntu 16.04. But now, every now and then, my computer freezes and I need to do a hard shutdown.

It seems to be freezing mostly on high memory usage. It freezes frequently when I am running eclipse. And it freezes EVERYTIME I try to start a Windows 10 virtual machine in VirtualBox (I have lowered the virtual machine RAM to 512MB and to 1 CPU, but it inevitably freezes).

I have check /var/log/syslog after the crashes, but it seems the crashes prevents anything from even being logged.

HARDWARE SPECS

[TABLE]
[TR]
[TD="class: sstitle, colspan: 2"]Computer[/TD]
[/TR]
 [TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]4x Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz[/TD]
[/TR]
 [TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]12205MB (2039MB used)[/TD]
[/TR]
 [TR]
[TD="class: field"]Operating System[/TD]
[TD="class: value"]Ubuntu 16.04.3 LTS
[/TD]
[/TR]
[/TABLE]

SCSI Disks ATA WDC WDS240G1G0A-
[TABLE]
[TR]
[TD="class: stitle, colspan: 2"]
OPERATING SYSTEM
[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 2"]VERSION
[/TD]
[/TR]
 [TR]
[TD="class: field"]Kernel[/TD]
[TD="class: value"]Linux 4.13.0-32-generic (x86_64)[/TD]
[/TR]
 [TR]
[TD="class: field"]Compiled[/TD]
[TD="class: value"]#35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018[/TD]
[/TR]
 [TR]
[TD="class: field"]C Library[/TD]
[TD="class: value"]Unknown[/TD]
[/TR]
 [TR]
[TD="class: field"]Default C Compiler[/TD]
[TD="class: value"]GNU C Compiler version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.6) [/TD]
[/TR]
 [TR]
[TD="class: field"]Distribution[/TD]
[TD="class: value"]Ubuntu 16.04.3 LTS[/TD]
[/TR]
[/TABLE]

---

### Post by cruzer001 on 2018-02-18
Thats a tough one.

Mixing ram can produce strange results.  What are you running?
```
sudo dmidecode --type memory
```

---

### Post by pedrovgp on 2018-02-18
```
Getting SMBIOS data from sysfs.
SMBIOS 2.6 present.

Handle 0x0040, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0041, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0040
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Hynix/Hyundai
    Serial Number: 0C8C284B
    Asset Tag: 9876543210
    Part Number: HMT351S6CFR8C-H9  
    Rank: 2

Handle 0x0043, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0040
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelA-DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown

Handle 0x0044, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0040
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: 0000
    Serial Number: 00000000
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: 2

Handle 0x0049, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0040
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelB-DIMM1
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
```

---

### Post by cruzer001 on 2018-02-18
Ok, ram looks doable, all that I can offer is suggestions (not necessary in this order):

Pull the 4gig stick and run on the 8G one.  Check that the sticks use the same voltage.

SSD
Check for BIOS update

Check BIOS for HHD/SSD settings.  AHIC/IDE/ATA power settings, I do not know what is right for your ssd.

If I think of something else, I'll post back.

Good luck

---

### Post by pedrovgp on 2018-02-18
Thanks for the tips cruzer001. I updated the BIOS, left only the 8gb stick, than only the 4gb stick, changed from AHIC to IDE and back again. But the problem persists. Everytime I start the virtual machine, the PC freezes.

Anyway, just wanted to give a feedback, thanks again for the help.

---

### Post by cruzer001 on 2018-02-18
Welcome :)
Lets look at other things.

Possibly you also updated your system before/after the hardware upgrade?  Try dropping back to previous kernel at boot (grub) in advance options.

What graphic driver are you running?
```
inxi -G
```

Do you have a guest account installed?  You won't be able to run your VM's but you could try to load it down.  See if it also crashes.

For testing purposes you could install a second desktop and try it; "Gnome Flashback (Metacity)".
[http://tipsonubuntu.com/2016/10/16/install-classic-gnome-flashback-ubuntu-16-10/](http://tipsonubuntu.com/2016/10/16/install-classic-gnome-flashback-ubuntu-16-10/)
Hopefully your system won't crash while installing this.

EDIT
Better yet, use the console for installing.
Ctrl + Alt + F1
At login or during the Unity session.

---

### Post by wildmanne39 on 2018-02-18
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by pedrovgp on 2018-02-19
Couldn't try the Gnome yet, but here is inxi -G result:
inxi -G
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Card-2: NVIDIA GF119M [GeForce 610M]
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 17.2.8

---

### Post by cruzer001 on 2018-02-19
Hello

Well as if you don't have enough to deal with.  The above printout suggest that there is a driver problem :(
Were going to ignore that for the moment.

The 4.13 kernel has been giving people a lot of grief lately.  Thats why I ask you to drop back to the previous kernel.  Its also been a reason for VirtualBox failures.  I bet you installed vBox from the Ubuntu sources (5.0).  People have found that 5.0 will not work with the 4.13 kernel.  The fix for most is removing it and downloading the 5.2 version from VirtualBox.  But lets ignore that for the moment too :)

Without a stable system, fixing the above is just not enough.  Got to have a stable system.

I propose using a different kernel.  The 4.4 kernel.  This is the kernel with long term support (5 years).  Right now your on the HWE stack which changes the kernel every 6 months.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

This download link will include the 4.4 kernel.
[16.04.1_64-bit_desktop iso]("http://old-releases.ubuntu.com/releases/16.04.1/ubuntu-16.04.1-desktop-amd64.iso")

Its not necessary to change anything yet.  Instead download the live iso and run it without installing.  You can either burn a DVD or use a flash drive.  You will be able to mount your existing install to access your files.  All were trying to find out is if this gives you a stable system.

---

### Post by pedrovgp on 2018-02-25
> **cruzer001 said:**
> 
Without a stable system, fixing the above is just not enough.  Got to have a stable system.

I propose using a different kernel.  The 4.4 kernel.  This is the kernel  with long term support (5 years).  Right now your on the HWE stack  which changes the kernel every 6 months.


I agree, virtualbox was not the biggest problem. I installed the 4.4 kernel with [Ukuu]("https://github.com/teejee2008/ukuu"). VirtualBox indeed started working. The system is a lot more stable, although I have experienced one or two crashes, mainly when using eclipse, firefox, terminals all in different desktops. But there I could not find a reliable way to reproduce the problem.

So, for now, it is working a lot better. Thank you a lot for the suggestion. I will post any update in case the problem occurs again.

> **cruzer001 said:**
> 
Well as if you don't have enough to deal with.  The above printout suggest that there is a driver problem :sad:
Were going to ignore that for the moment.

To be honest, I  thought my GPU was burnt. I used to play Skyrim in Windows and one day  my HDMI port stopped working and the game wouldn't run anymore. I just  assumed my GPU wasn't working.

Do you have any suggestion on how to solve this driver problem?

---

### Post by cruzer001 on 2018-02-25
Good, made some progress :)

Windows has its own drivers and Ubuntu supplies its own.  So there is no interaction between the two.

So in a nutshell, it could be your  card.  A video problem can cause lockups/freezes.  You can try installing a closed source driver.  Go to Software & Updates > Additional Drivers; reboot required.

You could also switch back to your integrated graphics for testing.

---

