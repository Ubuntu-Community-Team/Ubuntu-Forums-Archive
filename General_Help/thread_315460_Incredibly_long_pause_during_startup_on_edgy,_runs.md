---
title: "Incredibly long pause during startup on edgy, runs fine after that"
date: 2006-12-09
forum: General Help
---

### Post by mbryne on 2006-12-09
Greetings,

First of all thanks to everyone and their forum posts that have solved countless problems for me in the past, 

Unfortunately i havent been able to hunt down a solution for a problem I have been having:

During startup, the new ubuntu progress bar sits on about 1% for upwards of 3-5 minutes, after that long pause, the progress bar flies past and the desktop loads just fine, no more problems

is there anything that could be causing such a lengthy delay? where can I look (log files etc) to see what could be causing the problem?

Please let me know if you need any extra details

---

### Post by yopnono on 2006-12-09
Remove the splash from the grub menu.
It can be done by editing the menu.lst @ /boot/grub

Or at boot select the kernel and edit it for this boot only.
Select the kernel the press e to edit it and remove the splash from the line then press enter then b to boot.

---

### Post by mbryne on 2006-12-09
ok, thanks a lot for that, that narrowed it right down for me

it turns out it is a problem with the SATA controller, the error messages I am getting are as follows:

```


ata2: SATA max UDMA/133 cmd 0xF882E580 ctl 0x0 bmdma 0x0 irq 50
ata2: SATA link down (SStatus 0)
ata2: qc timeout (cmd 0xec)
ata2: dev 0 failed to IDENTIFY (I/O error)

```

It appears im not the first person with this error and a solution (compiling a newer kernel) was posted in another thread:

[http://ubuntuforums.org/showthread.php?p=1816768](http://ubuntuforums.org/showthread.php?p=1816768)


I was wondering if there is a solution that doesnt require compiling a new custom kernel?

---

### Post by yopnono on 2006-12-09
> **mbryne said:**
> ok, thanks a lot for that, that narrowed it right down for me

it turns out it is a problem with the SATA controller, the error messages I am getting are as follows:

```


ata2: SATA max UDMA/133 cmd 0xF882E580 ctl 0x0 bmdma 0x0 irq 50
ata2: SATA link down (SStatus 0)
ata2: qc timeout (cmd 0xec)
ata2: dev 0 failed to IDENTIFY (I/O error)

```

It appears im not the first person with this error and a solution (compiling a newer kernel) was posted in another thread:

[http://ubuntuforums.org/showthread.php?p=1816768](http://ubuntuforums.org/showthread.php?p=1816768)


I was wondering if there is a solution that doesnt require compiling a new custom kernel?

Is it only the delay at boot and if the computer starts. Then you can change the timeout for that service i guess. Until you find a solution for it.

Have a look in the /etc/init.d folder for the script that controls this.

Try to add *text* to the grub menu for more detailed info, and also remove the *splash* and also the *quite*.

Or you can add *timeout* in the grub menu to set the timeout, have never tried it. Have a look at the man for more info.
```
/usr/share/doc/usplash/README
```

---

