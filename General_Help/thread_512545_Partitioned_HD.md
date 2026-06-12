---
title: "Partitioned HD"
date: 2007-07-29
forum: General Help
---

### Post by phenom-lee on 2007-07-29
Hello, I have installed windows Home on my toshiba notebook, and then partitioned the HD to install Ubuntu fiesty fawn, after a problem wit windows (registration issue) on boot up I cant load windows, however ubuntu is working fine, how can I retrieve the data that was on windows if  ubuntu cant access the windows partition, is there a tool that I can use to recover the partition from Ubuntu side to get the mails and stuff??

---

### Post by coffeecat on 2007-07-29
Depending how you selected mount options when you installed Ubuntu, it may or may not be able to read the Windows NTFS partition already (but not write to it). If you can't find the Windows partition in Places > Computer or in /media or /mnt, you could post the contents of /etc/fstab and your partition layout and someone will help you edit fstab so that the Windows partition is mounted read-only on boot-up. That way you could read out and copy your files.

Alternatively, search the forum for the ntfs-3g driver which gives you read and write to NTFS. I have no experience of this but it seems that many forum members are happy with it.

---

