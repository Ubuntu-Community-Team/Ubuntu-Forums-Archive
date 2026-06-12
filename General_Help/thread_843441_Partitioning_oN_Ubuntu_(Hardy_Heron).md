---
title: "Partitioning oN Ubuntu (Hardy Heron)"
date: 2008-06-28
forum: General Help
---

### Post by Zach B on 2008-06-28
I recently installed Ubuntu and now I want windows back but there was a problem, I attempted to use my Windows XP and Vista discs and install it through the boot up menu and they didn't work for one reason, My main NTFS Hard Drive is gone. Ubuntu replaced with its own hard drive and Now I don't have a Hard drive. (C:\) I thought, Wouldn't it be possible to get it back if I made a new NTFS Partition for it, Without it I can't install Windows. I believe there is a Partitioner automatically installed on Ubuntu and I was wondering is there actually one on there and if there is where at?

I've heard about something called gParted but I can't find it. Also I'm new to ubuntu and I didn't know it was mostly command line based. That just makes installing things that much harder.

Please and Thank you,
Zach B

---

### Post by geirha on 2008-06-28
I don't know if creating an NTFS partition is going to help installing windows or not, but you can use gparted to remove your ubuntu partition and create an ntfs in its place. You cannot use gparted on a mounted partition though, so you need to boot up with the ubuntu CD (or get the ~60MB gparted cd), which has gparted preinstalled under System -> Administration -> Gnome partition editor (or something like that)

---

### Post by cdtech on 2008-06-28
You'll have to install gparted:
sudo apt-get install gparted

---

### Post by rraj.be on 2008-06-28
> **Zach B said:**
> 
I've heard about something called gParted but I can't find it. Also I'm new to ubuntu and I didn't know it was mostly command line based. That just makes installing things that much harder.

Please and Thank you,
Zach B


Yes.

Its defaultly installed in ubuntu.

Open Applications --> Accessories --> Terminal and type

sudo gparted

It will open.

If isn't already installed install it by typing this in terminal

```
sudo apt-get install gaparted
```

Then you will find more guide here on creating New partition

```
[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")
```

---

