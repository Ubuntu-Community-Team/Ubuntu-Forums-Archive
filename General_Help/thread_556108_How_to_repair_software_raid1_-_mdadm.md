---
title: "How to repair software raid1 - mdadm?"
date: 2007-09-20
forum: General Help
---

### Post by micro420 on 2007-09-20
I have a Linux software raid1 going on Ubuntu 6.06.  

/dev/sda + /dev/sdb = /dev/md0

I noticed that /dev/sda has a bad partition, fortunately it does not affect the boot partition.  I physically disconnected /dev/sda, but /dev/sdb doesn't boot.  NOt sure why.  Isn't a raid1 supposed to create an exact mirror, so I should be able to boot hard drive /dev/sdb, correct?  How do I fix this if I can't even boot /dev/sdb?  /dev/sdb has the good data.  I have a new hard drive waiting to be the new back up hard drive.  I want to turn /dev/sdb into /dev/sda, and put this new hard drive and make it into the new /dev/sdb.

---

### Post by Doc.Caliban on 2007-09-21
I'm sorry that I can't answer your question, but I have to ask you how you did this because one thing I miss from Windows was the RAID1 software I had.

I really just want to do certain folders, and on a removeable drive when it's plugged in.  Real time mirroring.

Can it be done?

-Doc

---

### Post by BeastlyKings on 2007-09-21
Actually, lol, I'd like to know how to do so as well.
My mobo doesn't support raid and I'd really like it :)

---

