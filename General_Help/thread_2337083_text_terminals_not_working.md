---
title: "text terminals not working"
date: 2016-09-14
forum: General Help
---

### Post by bardov on 2016-09-14
I installed from scratch 16.04, gnome + kde + unity. 
In all three environments switching to text terminals (ctrl alt F1..6) does not work

The display driver is nvidia (I installed the latest stable from nvidia).

I saw way too many posts on this, mostly on previous versions, but nothing seems to help.

My grub file looks like that:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset text"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=640x480

What else should I be looking at?

---

### Post by &amp;KyT$0P# on 2016-09-14
I have the same problem in 14.04.  It actually does work, but it just leaves you with a black screen.
[This bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/958891") looks related.

I just gave up and use the Intel graphics, works well for me.  If your machine has a Intel graphics card as well, something worth looking into.

---

