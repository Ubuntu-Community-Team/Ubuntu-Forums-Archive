---
title: "RAID 0, dual boot: Completely messed up PC"
date: 2013-02-15
forum: General Help
---

### Post by oxf77 on 2013-02-15
I had Windows 7 and Ubuntu Linux on a RAID0 disk- I deleted the Linux partitions (I think) using GParted, now when I boot I cannot get into Windows 7. I just get a grub error.

If I try and use the Grub Repair tool and put that on a USB stick to boot from, it says "BOOTMGR is missing"

If I boot the Win 7 CD and then go to do a repair it says "This version of System Recovery Options is not compatible with the version of Windows you are trying to repair"- although it is the same :s

How can I remove grub to boot windows normally??

Must I load the Live CD and repair grub from there? Can I not just remove grub and somehow get my PC to boot from windows directly?

EDIT In GParted (from the live CD) I only have my Windows 7 partition and an unallocated 1MB.

EDIT2 Just tried booting from Rescatux but I also get "BOOTMGR is missing"

---

### Post by Yellow Pasque on 2013-02-15
Will the Win7 CD at least let you drop to command prompt? [http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

(Oh, and thanks for reminding me why I hate Windows..)

---

### Post by oxf77 on 2013-02-15
> **Temüjin said:**
> Will the Win7 CD at least let you drop to command prompt? [http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

(Oh, and thanks for reminding me why I hate Windows..)

Nope, its the step just before that where I select the OS and then hit "continue" get the error about incompatible Windows installations:

"This version of System Recovery Options is not compatible with the version of Windows you are trying to repair"

---

### Post by oxf77 on 2013-02-15
Can someone walk me through how to re-install grub2 from the LiveCD? All the tutorials online assume you have a linux partition- whereas I only have a windows partition...

(I cant enter "sudo grub" either, says unknown command)

---

### Post by neerajkamaljit on 2013-02-15
do 1 thing boot wid windows 98 cd, k den type fixmbr dats it grub wil b removed:p

---

### Post by LostFarmer on 2013-02-15
> EDIT In GParted (from the live CD) I only have my Windows 7 partition and an unallocated 1MB.
  That might not be good.
I do not have Win 7 so can not be sure.  Every thing I have read says win7 will have at least 2 partitions, a small 1g boot partition and then the OS partition.  The boot files will be on the 1g partition. the OS partition alone will not be boot-able.

If the above is not correct but {Just tried booting from Rescatux but I also get "BOOTMGR is missing"} indicates it is, do you have any other comp that boot any MS windows with MS boot code in the MBR ?

Must ask , is this a EFI-GPT setup computer ?  or the old bios MBr booting (hoping) ? 

I am thing with a live cd can copy with 'dd' the boot code (only not partition table or hdd ID) from computer to computer.

Also do not have any knowledge with Raid.

---

### Post by oxf77 on 2013-02-16
Hi Guys,

I managed to fix it by re-installing Ubuntu in the space where the old Linux partition was.

I think this was messy because I am using a software RAID.

---

### Post by Mark Phelps on 2013-02-16
Good to see that it's fixed now. Please use the Thread Tools to marked this as SOLVED so others will see that.  thanks

---

