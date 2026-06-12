---
title: "hdparm usage"
date: 2007-05-13
forum: General Help
---

### Post by FizzBuntu on 2007-05-13
hi
I'm trying ot configure hdparm but didn't find any gui for it so used the command line.
According to what I read here and there, I shut down GDM to be in command line only.
Any of the parameters I entered gave me an " Inappropriate ioctl for device"
except for the readahead paramete.

Main main goal would not necessery be to have better performance, but to be able to make the 4 disks shut down when not used for a period and then generate less heat...

What did I miss?

---

### Post by 542 on 2007-05-13
Hi there,

Can you paste a sample command you're using which gives the error? 

Be aware that hdparm is only for IDE devices (/dev/hda etc. not /dev/sda).

---

### Post by FizzBuntu on 2007-05-13
ok thx, that must be the problem then, all my hdd are registered as /dev/sdx
The thing I don't understand is WHY ?
2 of the HDD are regular 40 Go IDE PATA drives (1 for the system, the other only for backup purpose - by the way does anyone know a good and simple backup software, I use to have ultrabackup on my winxp computer)
The other 2 are data storage on SATA...

Is there anything I can find to make the idle drive shutdown after a given time ?

---

