---
title: "How to copy entire hard drive"
date: 2008-04-03
forum: General Help
---

### Post by bellalamb on 2008-04-03
Hi

I am running Ubuntu Server 7.04

My hard disk is failiing - I need to duplicate the entire disk onto a new one.

How do I do that simply and quickly?

Thanks

---

### Post by kpkeerthi on 2008-04-03
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by ghostdog74 on 2008-04-03
a [reference]("http://www.softpanorama.org/Tools/dd.shtml")

---

### Post by hvc123 on 2008-04-03
use dd

---

### Post by zikade on 2008-04-03
Try PartImage - worked for me once.

---

### Post by dmizer on 2008-04-03
i like the free version of hdclone for a very easy, straight disk to disk bootable copy: [http://www.miray.de/download/sat.hdclone.html](http://www.miray.de/download/sat.hdclone.html)

obviously there are lots of options for you.

---

### Post by ericsante on 2008-04-03
boot off the CD as a live cd.

open shell prompt

scsi drives are /dev/sdX devices
IDE drives are /dev/hdX devices

so your command to copy a disk from scsi drive A to scsi drive B would be

dd if=/dev/sda of=/dev/sdb

for IDE drives it would be

dd if=/dev/hda of=/dev/hdb

---

