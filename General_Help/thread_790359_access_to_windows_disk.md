---
title: "access to windows disk"
date: 2008-05-11
forum: General Help
---

### Post by fabio61 on 2008-05-11
After a couple of attempts I succeded in installing ubuntu 8.04 with wubi on my computer. I decided to place ubuntu on my C: disk.

Besides my disk c: (with windows Xp) I have a couple of external hard disks (connected via USB).

After installation I can easily read my external disks (I found them neatly placed on my desktop) but I cannot find any way to access my old files on the main disk C:

any suggestion?

---

### Post by fabio61 on 2008-05-11
trovato: è in /host:lolflag:

---

### Post by ossobussi on 2008-05-11
sorry to bother you as a new ubuntu-user, but what do you mean with your answer.
Same problem to me, I installed wubi-Ubuntu an drive E:
and have no access to drive E:
which file do I have to edit in which way?

---

### Post by Thirtysixway on 2008-05-11
Go to Places > Computer and you should see one of the locations will be like "56.6 GB Media".  That would be your windows drive.  Of course yours won't say 56.6 GB but you'll see it.

---

### Post by Gripp on 2008-05-11
and if not, just go >'file system'>host and there you are. 

from the live CD it may be in media rather than host
but whatever disk you are running wubi from IS already there. has to be, or you wouldn't be running linux...

---

### Post by ossobussi on 2008-05-11
**Thanks for info** - it works. 

Nevertheless it makes me confused, because with wubi-ubuntu 7.04 the drive with installed ubuntu was mounted as other partitions as well. So I could see Partiion C / D / E on my Laptop. 

With version 8.04 I only see Partition C / D / and going the way >filesystem >host the Partition E with my datas and the ubuntu-system.

For your information: I installed it on Partition E because with my last installation with wubi 7.04 the installation crashed the complete filesystem - Boot-Logo started and Win XP stopped with BSOD. So I had to start the XP Recovery-Console, fix the MBR, start then with Win98, load Avira NTFS4DOS to access the NTFS-Filesystem, change the boot.ini - then restart and access ubuntu 7.04 so that I was able to recover some datas from the system-Partition. I hope wubi 8.04 will install itself better.

---

