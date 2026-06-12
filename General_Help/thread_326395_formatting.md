---
title: "formatting"
date: 2006-12-27
forum: General Help
---

### Post by Ubuntuud on 2006-12-27
Hi,

I just got a new usb flash drive...
And I would like to install Ubuntu on it.

I have already succeeded in that, but now I would like to use the livecdpersistence (or whatever it is called) feature.

I figured you'd need to have 2 partitions...
Gnome-Partitioner couldn't do it, so I used fdisk.
I created the two partitions, but now I need to format them.
But how?

I found I needed to do something like: 'sudo mkfs.vfat /dev/sdc1', but how can you specify the partion you wish to format?

If it is usefull, the stick has 1990 cillinders
every cillinder is 516096
making a total of 1027416576 -> 1027 MB
16 heads (translated) 63 sectors

the first partition is from the first cilinder to the 1350th
en the second from the 1351th to the last (1990)

Could anyone help me?
Thanks in advance!

---

### Post by ~LoKe on 2006-12-27
Boot up a LiveCD and mount the usb drive.  Format it with GParted.

---

### Post by Ubuntuud on 2006-12-27
But then why wouldn't it work with the one on edgy?
(that's what I'm running)

---

### Post by Ubuntuud on 2006-12-27
Well, I figured most of it out by myself. But how do you format fat16?
I tried 'mkfs.vfat16', 'mkfs.vfat', 'mkfs.fat16' but none of them gave the desired result...

I also couldn't find it with google...

---

### Post by elektronaut on 2007-03-04
```
man mkdosfs
```

---

