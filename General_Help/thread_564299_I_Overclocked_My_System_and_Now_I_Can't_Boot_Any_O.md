---
title: "I Overclocked My System and Now I Can't Boot Any OS."
date: 2007-09-30
forum: General Help
---

### Post by domat00 on 2007-09-30
I was able to get a stable overclock this evening, but now both my OS's are corrupted.  Windows XP gives me this error:  "\WINDOWS\SYSTEM32\CONFIG\SYSTEM file is missing/corrupted", and in ubuntu i get this error:  "crc error --system halted"

I can't lose either OS's, and I know this is a linux forum, and that's why I posted this at a PC forum as well.  I CANNOT lose either of these, there is too much in them for me to lose.  I also do not have my XP disc - I'm in another state.

I broke it!  But I believe with your help, I can tape it up!  :lolflag:

Please help!  I apologize in advance for breaking the cardinal rule of asking for help for a Windows OS, on a linux forum.

---

### Post by T3KN33K on 2007-10-01
Both of those errors are repairable. 

Assuming you have the install disks, just boot first from the Windows install disk, and run through the automatic repair utility.. it will look like its reinstalling a fresh version, but worry not, all of your settings/files/proggys are retained exactly as they were.  Then do the same with the Ubuntu Live CD, and you *should* be back to normal. 


If not, then a little more information may be of value.... at what stage of the boot (in either os) does the error occur?

---

### Post by scruff on 2007-10-01
Sounds like your bus speed is too fast for your RAM causing memory corruption. 

You should read the directions for resetting the BIOS to default in your motherboard manual. Generally, you can just pull the CMOS battery out of the MOBO, but sometimes there's a jumper and what have you. No big deal though, just reset the BIOS :)

---

### Post by domat00 on 2007-10-01
When I encountered the error (in initial boot sequence, just after selecting the OS from grub), the first thing I did was reset my BIOS.  I don't have my disc's for Windows (I'm in another state), so could you give me a walkthrough for repairing Ubuntu from the LiveCD?  I think I can salvage my development files from Windows if I could get into Ubuntu.

---

### Post by scruff on 2007-10-01
Can you boot from the LiveCD? Because if you can, but not from either OS on the hard drive, than OC'ing your system is likely *not* the cause of the problem. A bad overclock can completely be remedied by a CMOS reset, unless of course you've fried your CPU, chipset, etc. So if the live CD boots, at least we know your hardware likely wasn't damaged.

Probably the first step is to boot from the live CD and mount the Windows and Linux partitions so you can poke around a bit to see the extent of the damage. I *think* this gets done automatically from the Ubuntu live cd so start there and look around to see if you get any errors. 

Next thing I would do is perform a filesystem check and fix on your Ubuntu Partition. CRC errors (cyclic redundancy check) generally mean filesystem corruption that fsck may be able to fix.

I haven't really used Windows in the last 5 or 6 years so let's concentrate on getting Ubuntu fixed, then deal with Windows later. You're more likely to be able to repair a Linux install than a Windows one anyway. 

What type of filesystem are you using for Linux?

---

### Post by domat00 on 2007-10-01
Well I cleared my CMOS again just to make sure that there weren't any discrepancies, and tried to boot into Ubuntu once more.  This time it did an fdisk and it repaired the installation and I was able to boot into Ubuntu, so that's not a problem, and like you said I doubt it was the overclock that damaged the OS's.  I'll begin pulling my files from the Windows partition and see what I can do to repair it.

Thanks for your help.

---

### Post by scruff on 2007-10-01
Nice! Glad it worked out for you.

---

