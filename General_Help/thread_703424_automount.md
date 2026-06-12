---
title: "automount"
date: 2008-02-21
forum: General Help
---

### Post by ssyss on 2008-02-21
I`ve read lots of those threads, but didn`t understand anything what to do ! 
Can any one help to do the automount thing!

---

### Post by wolfen69 on 2008-02-21
what is it that you want automounted?

---

### Post by freelinuxhelp on 2008-02-21
To automount something it needs to be listed in the fstab file in the etc directory. (fstab stands for filesystem table.)
To add something to the fstab, run this in a terminal window:
sudo nano /etc/fstab

the fstab file has some info in it already. be sure not to delete any of it.
If you post exactly what you're trying to do, i might be able to give you the exact line for fstab

---

### Post by freelinuxhelp on 2008-03-08
Ever get this working?

---

### Post by MaDxCrEaM on 2008-03-16
I know I could use some help with this. I have two hard drives formatted to ext3.

First is /dev/sdb1 and when I mount, the mounting point is /media/Torrents

Second is /dev/sdc1 and when I mount, the mounting point is /media/usenet

I would love to get these automounted when I log in. Also, I create a mount --bind option, is there a way to automount something like that?

Thanks for any help!

---

### Post by jken146 on 2008-03-16
[www.psychocats.net/ubuntu/mountlinux](www.psychocats.net/ubuntu/mountlinux)

---

### Post by MaDxCrEaM on 2008-03-16
Thanks alot, that did it for me.

---

