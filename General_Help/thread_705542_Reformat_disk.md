---
title: "Reformat disk"
date: 2008-02-23
forum: General Help
---

### Post by dodgingspam on 2008-02-23
I'm having difficulties with my laptop and can only login with LiveCD. I'd like to reformat my entire hard drive and do a fresh Ubuntu install.

 Last time I did it when I had Windows, by going to command prompt and  typing format C:

Not sure how to reformat it with Linux. Any suggestions?

---

### Post by taurus on 2008-02-23
Use gparted in System -> Administration from the LiveCD to reformat your harddrive.

---

### Post by jeffus_il on 2008-02-23
There are a number of ways to do what you want to.
Probably the simplest and easiest is to install using the livecd and when you get to the disk partitioning section, tell the installer to use the whole disk and repartition, I forget the exact wording, you will find it there...

---

### Post by dodgingspam on 2008-02-23
Per-fect! It's formatting it now.

Thanks.

---

### Post by tke1384 on 2008-02-23
you could do "sudo dd if=/dev/zero of=/dev/your_device bs=1 count=1 this will write all 0 to your HD and then partition using fdisk but that's just how I would do it from command line

---

