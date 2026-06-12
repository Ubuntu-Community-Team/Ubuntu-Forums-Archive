---
title: "/dev/mapper/skapis-root usage 99%"
date: 2014-10-20
forum: General Help
---

### Post by tobislv on 2014-10-20
df -l command shows this statistics

[IMG]http://vega1.lv/_media/vega1-server.jpg[/IMG]

How can i free some space in /dev/mapper/skapis-root ?

---

### Post by O9aIevckc0 on 2014-10-20
it seems like you need to delete/move some files on your / partition probably files in /home

---

### Post by Impavidus on 2014-10-20
Have a look at this guide: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by tobislv on 2014-10-20
Thanks for replys guys. But if i take a look on 
/dev/sda1
/dev/sdb1 and
/dev/sdc1
none of them are 99%, then how / can be 99% ?

---

### Post by nerdtron on 2014-10-20
> **tobislv said:**
> Thanks for replys guys. But if i take a look on 
/dev/sda1
/dev/sdb1 and
/dev/sdc1
none of them are 99%, then how / can be 99% ?

Let's see more into your partitions. Please post the output of:
```
lsblk
df -Th
sudo blkid
```

---

### Post by tobislv on 2014-10-20
So here`s more info:
[IMG]http://vega1.lv/_media/more-info.jpg[/IMG]

---

### Post by nerdtron on 2014-10-20
Your LVM / partition is on sda5. So it seems here, your sda hard drive (could be your first hard drive) which is 698Gb is full.

---

### Post by tobislv on 2014-10-20
I think i figured out whats the problem. Thanks nerdtron for helping me.

---

