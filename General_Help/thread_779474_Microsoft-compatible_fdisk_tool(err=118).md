---
title: "Microsoft-compatible fdisk tool(err=118)"
date: 2008-05-02
forum: General Help
---

### Post by dreamlusion on 2008-05-02
Hello all,

I get this error right after I press "XUbuntu" on the OS selection menu.

I'm on Windows XP. I have downgraded from Vista (don't know if NTFS version has something to do with the error.)

thanks in advance!

---

### Post by tinybit on 2008-05-03
Press the INSERT key immediately after you select Xubuntu, single step trace the booting, and you may locate at which point the machine hangs.

Are you using a USB device as the installation media? Which wubi version are you using?

---

### Post by dreamlusion on 2008-05-03
Hi tinybit,

Thank you for answering! :)

I got this message using single step trace booting:

"Unrecognized partition table for drive 80. Please rebuild it by using a Microsoft-compatible fdisk tool(err=118)"

I found another post relative to this subject from the french ubuntu community:

[http://forum.ubuntu-fr.org/viewtopic.php?id=212023](http://forum.ubuntu-fr.org/viewtopic.php?id=212023)

Maybe it is the fact that I'm on a laptop and I (may or may not) have a custom MBR (I may have overwritten it).. I'll investigate towards this direction..

---

### Post by dreamlusion on 2008-05-03
I made sure that I have a standard MBR and not a custom one (I booted into Windows Recover Console and run fixmbr), but that did not help.

Tried to change the type of the hidden (D2D) partition to 07 (using PTEDIT32), but didn't help either

---

### Post by tinybit on 2008-05-03
Can you please show me the detailed info?

> 
Unrecognized partition table for drive 80. Please rebuild it by using a Microsoft-compatible fdisk tool


Normally this is not a serious problem, but a warning. I want to see what other messages displayed on the screen when the machine hangs.

Thanks for your report.

---

### Post by dreamlusion on 2008-05-03
tinybit hi!

this is the detailed output.

```

6305/16/63, Sector Count/Size=312581808/0, int13/08(80), version=0, C/H/S=1023/255/63, int13/02(80), err=0
Warning: Unrecognized partition table for drive 80. Please rebuild it by using a Microsoft-compatible fdisk tool(err=118). 

Current C/H/S=266305/255/63 LBA, C/H/S=266305/255/63, Sector Count/Size=-1677747/512
boot drive=80, int13/4B01(80), err=1, drive=80, Not CD
get_cdinfo(7F), int13/4B01(7F), err=1, drive=7F, cdrom_drive==FFFFFFFF.
Starting cmain()... Open /default... failure

```

it seems that my partition table is wrecked. Running PTEDIT32 (I could just run fdisk -l but I PTEDIT32 provides more information) shows that CHS values are (way) wrong...

Was it Windows XP Installation
Was it Wubi installation
Was it changing S-ATA mode in BIOS in order to install Windows XP (AHCI -> IDE)
Was it me running wubildr.exe (from within Windows XP)

...I don't know. But it must have been something from the list above, because I didn't do anything else that involves low level hard disk operations.

I tried to use open source software to repair my partition table (fdisk, testdisk, parted) but none seem to get the job done right. 

Partition Magic is not compatible (yet) with Vista partitions, so I'll try Acronis Disk Director Suite (10).. it's 70mb.. certainly not tiny ;)

---

### Post by dreamlusion on 2008-05-03
At least the cause was found. It was the Windows XP installation that messed things up.

[http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/6a0c4215a3564642](http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/6a0c4215a3564642)

Aragorn says (among other things): 

...I've heard
from many people that they've had trouble with partition boundaries when
installing GNU/Linux alongside Windows, and this dates back to the time of
Windows 2000...

Basically, if I understand well, there is nothing wrong going on.. The only reason I would want to "fix" this, is to get rid of the error message.

---

### Post by dreamlusion on 2008-05-03
I finally was not able to get rid of this annoying warning. I tried to manually set CHS for my partitions (testdisk reported the correct values) but I was not able to find a suitable tool that will perform this operation.

The one and only tool I found that could do the job, is the legendary PTEDIT32, but it wouldn't let me apply the CHS changes because my boot partition was after 1024 cylinder..

---

### Post by tinybit on 2008-05-03
So don't worry about this warning. And don't worry about grub4dos. Grub4dos won't touch your partition table.

If you would like, you may post your MBR sector and I could fix it for you.

I only need to see your partition table which is in the ending 66 bytes of your MBR.

At the grub4dos prompt, type this to display your MBR:

cat --hex (hd0)+1

---

### Post by dreamlusion on 2008-05-04
WOW, I'm impressed by the fact that although I'm sure you have better things to do other than fixing my partition table, you are willing to do so! 

Thank you very much tinybit for being so kind, maybe I'll try it my self ;)

---

