---
title: "Mount AIX hard drive"
date: 2008-02-03
forum: General Help
---

### Post by tgunner on 2008-02-03
I'm in the process of trying to rescue an IBM RS/6000. It has a 4gb SCSI hard drive with AIX installed. I have the drive showing up in Ubuntu as /dev/sdb. What do I do now to mount it, and browse the files on it?

---

### Post by tgunner on 2008-02-03
I forgot to mention that the drive *is* connected to a SCSI controller in my ubuntu machine, it is not in the RS/6000. I'm pretty sure the file system used is JFS, so if someone could just tell me how to mount the hard drive, I can probably get the rest.

---

### Post by articpenguin on 2008-02-06
what aix version is it? If it is JFS1 then you cant mount it. The linux JFS version is JFS2.

---

