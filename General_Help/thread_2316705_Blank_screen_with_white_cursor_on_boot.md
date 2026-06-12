---
title: "Blank screen with white cursor on boot"
date: 2016-03-10
forum: General Help
---

### Post by josh159 on 2016-03-10
I'm running Ubuntu 14.04 on an SSD. One day when powering up the  system, the boot halted on a blank screen with a blinking white cursor.  Holding shift while booting to see Grub menu does not work. I also tried  booting from the live CD to access the disk. The live CD works, but  when I open software or the terminal the SSD is detected as having only  20Mb of unallocated space.


  I would like to salvage the information on the drive, but if it's not  possible, I would at least like to be able to use the SSD again as my  primary boot device. 


  Any thoughts? Thanks!

---

### Post by jim_deadlock on 2016-03-10
Instead of holding shift for GRUB, try tapping the down arrow.

---

### Post by ajgreeny on 2016-03-10
Is this a UEFI or BIOS machine?

If UEFI you may need to repeatedly tap Esc at power-on to get to the grub menu, though I have to admit that I have found it almost impossible to get the grub menu to show by pressing anything at power-on on my single OS UEFI machine without making changes to the /etc/grub/default file.  I have tried Shift, Esc, Up, Down, various F# keys all to no effect.

Here's my /etc/grub/default file with my reminder lines shown in red
```
GRUB_DEFAULT=0
[COLOR="#FF0000"]#Next line will make the countdown time show menu by default[/COLOR]
[COLOR="#FF0000"]#GRUB_TIMEOUT_STYLE=menu[/COLOR]
[COLOR="#FF0000"]#Next line changed from 0 to 2 for 2 second delay[/COLOR]
GRUB_HIDDEN_TIMEOUT=0
[COLOR="#FF0000"]#Next line changed from true to false to allow delay countdown to show[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR="Xubuntu-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by mastablasta on 2016-03-10
I don't know about salvaging data, but you can use something like ultimate boot cd or similar to do a SMART test, see if the disk is OK. it is possible that a similar rescue/diagnostics/repair disk is offered by disk manufacturer. maybe it just needs fsck to be run. hard to say at this point without more data.

can you actually see data on SSD disk from live session?

---

### Post by josh159 on 2016-03-15
The mobo website (ASUS Z-170K) has this detailed BIOS info:

128 Mb Flash ROM, UEFI AMI BIOS, PnP, DMI3.0, WfM2.0, SM BIOS 3.0 ACPI  5.0, Multi-language BIOS, ASUS EZ Flash 3, CrashFree BIOS 3, F11 EZ  Tuning Wizard, F6 Qfan Control, F3 My Favorites, Quick Note, Last  Modified log, F12 PrintScreen,  and ASUS DRAM SPD (Serial Presence  Detect) memory information

I don't know the difference between UEFI or BIOS machine

---

### Post by fantab on 2016-03-15
Booting the LiveUbuntu can you post the output of the following from Terminal?

```
sudo parted -l
sudo df -h
```

Much better if you can post your [BootInfo Summary]("https://help.ubuntu.com/community/Boot-Info"), using [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool.

---

