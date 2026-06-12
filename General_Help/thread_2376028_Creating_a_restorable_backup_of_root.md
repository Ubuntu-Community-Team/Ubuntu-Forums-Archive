---
title: "Creating a restorable backup of root"
date: 2017-10-29
forum: General Help
---

### Post by Peter_Brandon on 2017-10-29
I installed Ubuntu without using LVM.  In order to use a SSD cache, apparently I need LVM on my root and home partitions, and I gather that to convert my directories to LVM, I will need to reformat them.  But, I'd like to do this without having to reinstall all my software from scratch.  I have an external HD on which I previously installed a bootable copy of Ubuntu, though haven't sought to install all my internal HD software on that.  

So suppose I were to copy all my root partition files from my internal to external HD with rsync.  If I then reformatted my internal root partition and copy the files back from the external HD, does anyone know whether I could expect all my software (and my computer) to still be working?  I can use the update flag in rsync so that already existing files on my external HD aren't replaced.  I'd probably have to make some special provisions to insure the fstab files on both disks don't change.  But beyond that, would this work or am I missing something?

---

### Post by monkeybrain20122 on 2017-10-29
Use fsarchiver, it is in the repo. [http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/)

---

### Post by Peter_Brandon on 2017-10-30
Thanks, that looks very helpful!  Hadn't considered an archiver.

One question:  Is it ok to backup even with the OS running or do I need to backup with the OS shut down?

Your solution doesn't quite give me a working copy of my software on my external HD as might the rsync solution.  But I can use fsarchiver to create a backup in case anything goes wrong with the rsync solution....

---

### Post by speartip on 2017-10-30
It is best to use fsarchiver on a partition that is unmounted. So if you dual boot with another Linux OS, you can archive from there.
Alternatively you can boot from something like SystemRescueCD, and archive your partition from that.
[http://www.system-rescue-cd.org](http://www.system-rescue-cd.org)

---

### Post by monkeybrain20122 on 2017-10-30
> **Peter_Brandon said:**
> 
One question:  Is it ok to backup even with the OS running or do I need to backup with the OS shut down?

You can backup when OS is running if you use the options -a and -A with the savefs command
sudo savefs -a - A ...

> 
Your solution doesn't quite give me a working copy of my software on my external HD as might the rsync solution.  But I can use fsarchiver to create a backup in case anything goes wrong with the rsync solution....

You must be doing something wrong then, I routinely move Linux installation around different HD with fsarchiver.

---

### Post by Peter_Brandon on 2017-12-10
Haven't been on in a while, but just wanted to say that fsarchiver worked like a charm!  Good compression, fast, and restores quickly and with no issues whatsoever.

---

