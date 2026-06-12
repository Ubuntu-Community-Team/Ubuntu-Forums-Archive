---
title: "Grub Rescue error after installing windows 10"
date: 2017-04-04
forum: General Help
---

### Post by alexischalut97 on 2017-04-04
[COLOR=#111111][FONT=Ubuntu]Hello so i've got a problem with my computer... here is my problem: i tried to install windows 10 (was on Windows 7 before, so i did the "migration") and ubuntu 16.04 was instal in dual-boot... (not shure about the version of Ubuntu anymore :/ ) and now my computer start and BAM Grub error... 

i've tried to do the ls (show me this: (hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) (fd0). Then ls (all of them) and i got the error; Error: Filesystem is unknown. But there is this one the (fd0) witch take some time to load and then it shows me this error; Error: Failure reading sector 0x2 from 'fd0'.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What can I do ? I also have an another disk that i unpluged when this happen... but i think my ubuntu was on it... but when i plug in him, i get: (hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos5) (hd1,msdos1) (fd0) (so 2 more partitions ?) again, doing ls on each of them do nothing... i also tried with the set prefix and set boot stuff but nothing happen... the only thing that do something is my (fd0) but it give me an error i don't know O_o Note that if i unplug the main disk (the one with all the (hd0)), the computer doesn't load GRUB... So the Grub is on the HD0 but my ubuntu i'm pretty shure it was on my hd1...

Thanks for the help[/FONT][/COLOR]

---

### Post by yancek on 2017-04-04
If you were using windows 7 with the older MBR boot system, then your windows installer has overwritten the Grub boot code in the MBR.
The installer will not ask you if you want to do this.
The installer will not inform you this will be done.
Trying to boot Ubuntu/Linux from a windows bootloader is possible but is a very convoluted process.
Best option is to reinstall the Ubuntu Grub bootloader to the MBR of the drive on which you have Ubuntu.  
It's difficult to be any more detailed without more specifics on your drives/partitions so you might go to the site below and get the boot repair software, burn it to a flash drive or CD, boot with it and select the Create BootInfo Summary option and post a link to the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by alexischalut97 on 2017-04-04
Oups sorry... i fixed my problem... I use the Repair-Boot (that i put on a live-usb) and just do the fix... Now i can access my windows back normally... Thanks for the help anyway :)

---

