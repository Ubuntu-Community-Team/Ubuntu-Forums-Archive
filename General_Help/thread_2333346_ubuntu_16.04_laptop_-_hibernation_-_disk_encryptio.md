---
title: "ubuntu 16.04 laptop - hibernation - disk encryption"
date: 2016-08-09
forum: General Help
---

### Post by deb2014 on 2016-08-09
Hello,I recently installed ubuntu 16.04 and decided to fully encrypt my SSD hard drive.

I did so by creating one small separate /boot partition and another one encrypted with luks split in 4 logical volumes : swap /root and /home.

It works well except that hibernation randomly crashes. I goggled the issue several times, tried to several hibernation tools (uswusp, tuxonice), nothing improves.

I tested the hibernation process with another partition, a real one not just a logical volume. I still get some crashes if I encrypt the partition, tried several ciphers,
 but it works well if I keep it unencrypted, I can hibernate ten times one after the other, which never happened otherwise.

There is no clear debug messages when crashes occur, some "general protection fault", it seems that with encryption the hibernation image gets corrupted in some way.

So, I can get hibernation working, but at the expense of lesser security, that is to say the hibernation image does not ask me the /root /home encryption key on resuming.

Is there a way to close the encrypted partition during the hibernation process, so that the resuming process asks again the passphrase (like when booting) even if the
hibernation image is not encrypted ?

Thanks for your help

Regards

---

