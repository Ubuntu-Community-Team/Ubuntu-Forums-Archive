---
title: "BIG TROUBLE. Power lost during Install"
date: 2012-11-19
forum: General Help
---

### Post by lemonoid on 2012-11-19
I made a bootable USB of 12.10 installation, inserted it and began to install 12.10. Well it seemed that the power company for some reason didn't process our payment and it just so happened that WHILE 12.10 was installing, the power shut off for the whole apartment. When the power was turned back on, I booted up the PC, with the Ubuntu USB still in. This time when it got to the Live menu, I was not allowed the ability to switch between "install" "try" or whatever the options are when you initially boot a bootable Ubuntu USB made by UNetbootin. Instead it went straight into Live Ubuntu 12.10. So I was like okay cool, i will just press the 'Install Ubuntu 12.10' Icon on the desktop and do it from there. My mouse was responding to my movement, but nothing on the desktop worked. When I clicked the icon, nothing happened. When I tried to open the Application window or whatever its called nothing happened. In short, nothing was responding to my mouse clicks. I tried to click the upper right icon to shut down the computer and that did not respond either. So I used the button on the back of my PC to power down the PC. When I booted back up, it did not read the USB. I tried putting in my 12.04 DVD and it did not read that. I tried putting in Boot-Repair, it won't read that. I made a Super GRUB Disk 2 on my girlfriend's laptop, it won't read that. For some reason, it won't read any form of software (My HDD with Windows 7, DVD's, USB's, etc). The only thing it does is go to the ```
grub rescue > 
``` command line. I do NOT know what to do. Can ANYONE help me come back from this? The only command that has worked at that command line was ```
ls
``` I found this ```
set root=(hd0,msdos6)
set prefix=(hd0,msdos6)/boot/grub
insmod normal
normal
``` elsewhere and it didn't work. it said 'normal' is not a file. I have no clue what to do here. I'm sure that is is not completely messed up if I could just get a bootloader to load some type of media, then I would be ok. Actually at the top of the black screen with all this data (PCI device listing...) on it where the grub rescue command line is shown, it says 'USB Storage Device: SanDisk SanDisk Cruzer 8.02' so I  know that the desktop is taking in the media, its just not processing it. Does anyone have enough experience with this grub rescue> command line to help me be able to fix this??
(this whole problem stemmed from an upgrade from .04 to .10 that corrupted so I've been having nonstop problems for a day now and I'm ready to have Ubuntu back :( )

---

### Post by YannBuntu on 2012-11-19
Hello
Broken install/upgrade lead to missing / broken system files. SOlution is to fix system files via an Ubuntu disk this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

in your case, i would use a 12.04 disk, as the Unity version included in 12.10 seemed to bug with your hardware.

---

### Post by Bashing-om on 2012-11-19
In a situation such as described, I would  be deeply concerned with data corruption in the new upgrade:
I suggest a fresh/clean install. (try and save desired files thus)

As power failure : bios settings ? -> reset in bios to factory defaults.
reset boot device priority 1 to the booting device:
attempt then to boot the install medium in "try" mode
Nautilus file manager-> copy any found files to backup medium 
install ubuntu ( hope ya not dual booting).
[INDENT]just my 1 pounds worth ==> BDQ

[/INDENT]

---

### Post by efflandt on 2012-11-19
For many computers, to boot removable media, even if you set CD/DVD or USB before internal drive, you might still need to press a hotkey (often F12, sometimes another key like Esc) during BIOS splash screen to select boot device.

The fact that it goes to the grub prompt would seem to indicate that it is booting your internal hard drive, but grub was not completely installed yet.

You might want to consider getting a UPS (uninterruptable power supply) to avoid unexpected shutdowns.  That might not last long enough to complete an install, depending upon how far along it is, but can avoid power out data corruption at other times.  My power went out recently when some clown hit the front steps of a small church, tore off the corner of the building exposing the mens room, and the vehicle ended up on its roof.  With backup power I had plenty of time to shut my system down.  But it reminded me that I needed to get replacement batteries for the UPS that supplies my DSL modem, wifi, and other network equipment in my basement.

---

### Post by lemonoid on 2012-11-19
> **Bashing-om said:**
> In a situation such as described, I would  be deeply concerned with data corruption in the new upgrade:
I suggest a fresh/clean install. (try and save desired files thus)

As power failure : bios settings ? -> reset in bios to factory defaults.
reset boot device priority 1 to the booting device:
attempt then to boot the install medium in "try" mode
Nautilus file manager-> copy any found files to backup medium 
install ubuntu ( hope ya not dual booting).
[INDENT]just my 1 pounds worth ==> BDQ

[/INDENT]

Yeah I tried to go in and reset BIOS to default settings and then try it. Which places the internal HDD as 1st boot priority, and CD-ROM as second, ans USB-HDD as third. Then I put in the media, it didn't work. I don't know what I did, but now when I get to the 'black screen' the ```
grub rescue>
``` prompt will not even take my input! when I type nothing happens!!! this SUCKS. because I think I figured out how to fix it from that prompt, then I take a nap and wake up and I can't even type in the command prompt. if this helps anyone with advanced knowledge of this subject, the screen doesn't say: no such partition found or no such disk found like it does when you can just pop in boot repair it says ```
error: file not found
```
the data immediately preceding the l ines of file not found. says
```
Verifying DMI Pool Data .......... 
```, and above that it has a PCI device listing show Bus No., Device No., Func No., Vendor/Device, Class, Device Class, and IRQ. Is there any way to just reset my MBR back to the way it came?? As when it only had Windows on it because when it had Windows on it, there would be now grub rescue showing.

---

### Post by stinkeye on 2012-11-19
-

---

### Post by lemonoid on 2012-11-20
> **stinkeye said:**
> -
is this supposed to be a response, or are you just trying to up your bean count?


UPDATE::::
ANYWYAS>>>> I have repaired my device. The way that I did this was by going into my BIOS and then CMOS Settings and enabling ESCD which offers some type of extra support during the event that you are not able to boot into ANY OS, and that was my problem. That's what I did, and I changed a couple of other options in my BIOS that really aren't significant to this, and I was then able to boot live media again, and fix my system. I really don't know what happened, somehow I believe during the installation of 12.10 (where my power got shut off) that something was installed into the MBR that messed it up, and ESCD was able to revert and fix it.

---

### Post by stinkeye on 2012-11-20
> **lemonoid said:**
> is this supposed to be a response, or are you just trying to up your bean count?



No, I had written to just select your usb as first boot in bios and reboot with usb inserted but seen it had already been said.

---

