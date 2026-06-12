---
title: "uninstall linux/grub"
date: 2007-11-06
forum: General Help
---

### Post by carrick149 on 2007-11-06
i need to restore my laptop to origonal settings using pqservice.  to do this, i need to put my partitions back the way they were before i put on linux.  therefore, i must delete linux and get back my acer mbr.  i need the acer mbr so i can activate the restore thing with alt+f10 at startup.  apparently i can also move grub's menu.lst so that it is still intact when i delete linux.  i am open to either, i just want to get my computer working again.
thanks,
matt

---

### Post by Shazaam on 2007-11-06
From a quick look at Acer's site you needed to make recovery disks for any restore function to work. If you didn't make the disks you might be out of luck. You could try contacting them for an answer.
Look at this...

[http://global.acer.com/support/winvista/faq.htm#q0008](http://global.acer.com/support/winvista/faq.htm#q0008)
Q8. Pertains to Vista but would be the same for Ubuntu.

also see this...
[http://www.notebookforums.com/archive/index.php/t-139963.html](http://www.notebookforums.com/archive/index.php/t-139963.html)

---

### Post by carrick149 on 2007-11-06
i have a restore partition.  it only works if the partitions are right.  i need to get rid of linux and either replace grub with the origonal mbr, or move grub to a windows partition so i can make the partitions right.  don't worry about restore disks, i have already worked that part out.

---

### Post by Shazaam on 2007-11-08
Is there a way to boot the recovery disk and do a "fixmbr" and "fixboot" like you can with a retail version of Windows?

---

### Post by kellemes on 2007-11-08
Get [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and restore the MBR.

---

### Post by carrick149 on 2007-11-08
will that put back the origonal mbr? (super grub disk uninstall grub option)  i need the specific acer mbr so i can load pqservice.  just so you know, i've hardly used anything other than windows and really don't know linux.

---

### Post by kellemes on 2007-11-08
> **carrick149 said:**
> will that put back the origonal mbr? (super grub disk uninstall grub option)  i need the specific acer mbr so i can load pqservice.  just so you know, i've hardly used anything other than windows and really don't know linux.

I only know SuperGrubDisk can restore the MBR using Grub or put the Windows-bootloader back..
I can't answer your specific question.. don't know about pqservice.. sorry.

---

### Post by carrick149 on 2007-11-08
well, will it put the original windows bootloader back (ie one backed up from before), or just a default one?

---

### Post by Maestro23 on 2007-11-08
> **carrick149 said:**
> well, will it put the original windows bootloader back (ie one backed up from before), or just a default one?

I googled up (restore acer mbr) the following link.  Might put you on the right path. If you have seen it already, sorry.

[http://forum.notebookreview.com/showthread.php?t=74919](http://forum.notebookreview.com/showthread.php?t=74919)

Good luck.

---

### Post by carrick149 on 2007-11-09
i already tried that, it didn't work on multiple levels

---

