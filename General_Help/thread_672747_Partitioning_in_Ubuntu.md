---
title: "Partitioning in Ubuntu"
date: 2008-01-19
forum: General Help
---

### Post by kernel89 on 2008-01-19
Hey, 
I fully removed my Windows partition to expand my Ubuntu Partition. But I'm now left with my ubuntu partition along with its swap partition and a single large ext3 partition.
I want to extend my Linux partition by adding the excess ext3 partition.
Usually in windows I would delete the excess partition and resize the windows partition.
But I can't do that with this app. I'm using the gnome partition editor.
Thanks in Advance!

[img]http://img263.imageshack.us/img263/6910/screenshotwn0.png[/img]

---

### Post by p_quarles on 2008-01-19
Delete /dev/sda1. You can only expand an existing partition into unformatted free space.

---

### Post by kernel89 on 2008-01-20
Yeah, I know, as I said, I can't expand the ext3 in which Linux is installed, because I have to unmount it first, and it wont let me.


[img]http://img250.imageshack.us/img250/7302/screenshot1ue6.png[/img]

---

### Post by p_quarles on 2008-01-20
So, you're running Gparted from the same hard drive that Ubuntu is installed on? That won't work, simply because you cannot unmount the partition from which the OS is running.

Try the [Gparted Live CD]("http://gparted-livecd.tuxfamily.org/").

---

### Post by kernel89 on 2008-01-20
Is it graphical, for I am a newbie.
edit* nvm [http://gparted.sourceforge.net/larry/livecd/screenshots/gparted-livecd-0.3.4-5.jpg](http://gparted.sourceforge.net/larry/livecd/screenshots/gparted-livecd-0.3.4-5.jpg)

---

### Post by Sef on 2008-01-20
> Is it graphical, for I am a newbie.

Yes it is.

---

