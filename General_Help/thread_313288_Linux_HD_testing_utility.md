---
title: "Linux HD testing utility?"
date: 2006-12-05
forum: General Help
---

### Post by artinla on 2006-12-05
Is there a native linux application that will allow me to test the integrity of a hard drive like W32 Spinrite/NDD/WDDiags/etc do?

I don't mean a bootable CD such as Seatools, but an installable app that I can use to diagnose a failing drive from within my Ubuntu environment?  I really prefer something generic that doesn't require me to have a specific brand of drive.

If there is some command line thing that I can do to accomplish this, I would be interested in that as well.

Also.. DD is very slow to clone a drive since it copies bit for bit, copying free space in addition to all the files.  Is there a way to clone a drive within Ubuntu that will copy all files and the MBR, recreating the partition structure automatically such that I can dump that onto a new drive without a million commands?  Something like Norton Ghost does?  I know that you can create all the partitions, tar the files and extract them onto the new partition, then install grub.. but that seems mighty cumbersome and there must be an easier/quicker way.

Thanks,

Art

---

### Post by artinla on 2006-12-06
Nothing?!  Wow, I didn't think that testing a HD was such an odd thing to want to do.

Arrgh.

Thanks anyway.

Art

---

### Post by artinla on 2006-12-07
Still looking.  If the above a dumb question, could someone tell me why?

Thanks

---

### Post by electronpusher on 2007-01-23
I hope it's not a dumb question because we both appear to have the same problem. I did put a question about hard drive testing on before and I'm still having trouble. Based on what LITTLE I know there is a utility called e2fsck that looks like it ought to work but it seems like a very intimidating command. The man page says that if you don't use it correctly it can wipe out all the data on your drive. Any ideas or suggestions? HELP! I'm also new to using these internet forums so please forgive me if I've made any blunders!

Richard.

---

### Post by der_joachim on 2007-01-23
I do not know the programs mentioned above, but have you tried badblocks? Additionally, AFAIK any SMART-capable disk can be monitored. Look for the package smartmontools.

---

### Post by robenroute on 2007-01-23
If you want to thoroughly test HDDs, most manufacturers offer downloadable utilities (often running of a boot floppy; I know, I know, awfully way-back-when stuff) that offer extensive analysis of HDDs.

---

### Post by robenroute on 2007-01-23
> **artinla said:**
> I don't mean a bootable CD such as Seatools....

I guess, I only half-read your posting.... Sorry.

---

### Post by tronica on 2007-01-23
there is a tool for benchmarking a drive.

> apt-get install bonnie++

then to start type

> bonnie++

keep in mind this will really stress your drive

---

### Post by malathion on 2008-06-05
I found this, hope it helps anyone with similar problems.

[http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

---

### Post by greco8523 on 2008-06-20
I'm sure there is a linux version of seatools you could use? I rememebr seeing it about 2 years ago -  well it's only useful if your drive is a seagate.

---

