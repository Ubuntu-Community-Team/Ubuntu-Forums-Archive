---
title: "K3b hangs Feisty and causes file system errors"
date: 2007-11-07
forum: General Help
---

### Post by x1a4 on 2007-11-07
Hi,

Recently I began experiencing serious problems with K3b.  When I start it, after about 10-15 seconds of displaying the splash screen the whole system hangs.  When I do a hard reset I get file system errors (on multiple file systems) which I have to fsck using the Ubuntu CD before I can boot.  The drive itself works correctly, as I can read from it as well as write using the CD.  

When running K3b from a terminal I get the following right before the system hangs: 

(K3bDevice::ScsiCommand) failed:
   command: MODE SELECT(55)
   errorcode: 72
   sense key: MEDIUM ERROR(3)
   asc: 0
   ascq: 3



I also get the following ata2 error associated with this event: 


ata2: port failed to respond (30 secs, Status 0xd0)
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd a01/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x4a data 8 in


The problem is not the CD itself as I've tried running K3b with several brand new ones and with no CD in the drive.  Since I can write from the Ubuntu CD, I suspect it's a problem with the ata2 kernel module.

Thank you.

EDIT: Initially, the copy of K3b I had installed was from the standard repositories, then, when this happened for the first time, I reinstalled K3b from the backports repository and it worked.  I was able to run K3b and use it to write to a CD, therefore I assumed it was a K3b bug.  But subsequent tries kept hanging my system.

---

### Post by RTrev on 2007-11-07
For what it's worth, I've been hearing a **lot** of people having problems with K3B, and not just on Ubuntu.  Not sure if they just released a broken cut or what.

---

