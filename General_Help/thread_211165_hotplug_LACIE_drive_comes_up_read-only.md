---
title: "hotplug LACIE drive comes up read-only"
date: 2006-07-07
forum: General Help
---

### Post by conanjb on 2006-07-07
When I hotplug my USB LACIE drive, it is recognized by the OS (Drapper Drake 6.06). If I look in /media I see  that the OS recognizes it and I see the following:

> 
drwx------ 14 conanjb conanjb 32768 1969-12-31 16:00 LACIE/


When I try to write to the drive I get the following message:
Can't open file: .... Read-only File System

I moved from SuSE to Ubuntu and hotplugging the LACIE under SuSe always allowed me to write to the drive.

Any suggestion?

TIA,

gary

---

### Post by aysiu on 2006-07-08
What filesystem is it?

---

### Post by conanjb on 2006-07-08
The filesystem is FAT 32.

gary

---

### Post by aysiu on 2006-07-08
That's weird. FAT32 should come up as read/write.

We could always force it to mount that way:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Kind of a dumb workaround, but that's all I can think of right now.

---

### Post by testube_babies on 2006-07-08
I had the same problem and solved it by deleting the line that refers to the drive in /etc/fstab and then rebooting.  I'm not sure exactly how "safe" it was to do that, but it worked nonetheless.

---

