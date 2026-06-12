---
title: "Can't change drive I/O setting to 32 bit"
date: 2008-03-07
forum: General Help
---

### Post by Oldest Bob on 2008-03-07
hdparm works well to baseline my hard drive using" hdparm -tT /dev/sdb " I found that my drive setting was defaulted to 16 bit so tried to change it with hdparm -c3 /dev/sdb. I got message that "HD_SET_32BIT failed: invalid argument." Can anyone tell me how to get changes to my I/O settings. I do have an SCSI drive as noted. Oldest Bob

---

### Post by astrotech226 on 2008-03-07
I don't know about the 32 bit setting, but hdparm wasn't originally intended for scsi devices, although some options may work.  Here's an excerpt from the man pages:

> Although this utility is intended primarily for use with (E)IDE hard disk devices, several of  the  options  are  also  valid (and permitted) for use with SCSI hard disk devices and MFM/RLL hard disks with XT interfaces.

Another option would be to check out "sdparm", but you'll probably have to install it.

```
sudo apt-get install sdparm
```

---

### Post by disturbedite on 2008-03-07
why not just edit hdparm.conf?  thats what i did to enable dma & 32bit access & it worked fine.

---

### Post by Oldest Bob on 2008-03-07
Astrotec226 Thanks for idea. I installed sdparm but it isn't a parallel to hdparm. So ever onward Oldest Bob

---

### Post by Oldest Bob on 2008-03-07
Disturbedite - Thanks much also- but I tried that to no avail. I think Astrotech 226 had the right idea - hdparm is for IDE drives and not scsi. Why it gives a timing output but nothing else I don't know. I edited hdparm.conf and it now shows muti_set_io=32 in all areas but when I run hdparm it says that the value is "default=16bit". Ubuntu is working well and  I'm not any kind of a geek so I'll just leave well enough alone. Oldest Bob

---

### Post by disturbedite on 2008-03-10
> **Oldest Bob said:**
> Disturbedite - Thanks much also- but I tried that to no avail. I think Astrotech 226 had the right idea - hdparm is for IDE drives and not scsi. Why it gives a timing output but nothing else I don't know. I edited hdparm.conf and it now shows muti_set_io=32 in all areas but when I run hdparm it says that the value is "default=16bit". Ubuntu is working well and  I'm not any kind of a geek so I'll just leave well enough alone. Oldest Bob
good idea.  if you don't know what you're doing (not that i do, insofar as scsi is concerned) it is wise to leave well enough alone.

---

