---
title: "Problem in installing the latest Ubuntu"
date: 2008-01-01
forum: General Help
---

### Post by kris2pe on 2008-01-01
After installing the OS. Ubuntu doesn't seem to boot up!
It give some sort of error. I can't seemed to error remember.
The error occurs when Grub is suppose to start w/ its dual boot selection!

---

### Post by Sef on 2008-01-01
So you start to boot and when you have a choice to boot, you get an error instead of getting a choice of which os to boot?

---

### Post by kris2pe on 2008-01-01
Yup error loading Operating system 
is the message!

---

### Post by Sef on 2008-01-01
Could be a problem with GRUB.  Easiest way to fix it would be to download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  It is easy to use.

---

### Post by kris2pe on 2008-01-01
How do you propose I do that if I can't even access both os?
I'm using live cd now!
Live cd is pretty nifty! :( Especially if ubuntu really f-up! 
and how the hell am I going to use that?

---

### Post by Sef on 2008-01-01
Check out [Recovering GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Can you access your hard disk with your live cd?  If you can then you should be able to download SGBD to there and burn from there.

---

### Post by kris2pe on 2008-01-01
I've manage to get ubuntu working.
But my windows I can't make windows work.
What do I do w/ that?

---

### Post by Sef on 2008-01-01
Application > Accessories > Terminal

```
sudo fdisk -l
``` (small L)

That will show your partitions.  Paste a copy of it here.

---

