---
title: "Ubuntu Studio WILL NOT UNINSTALL!"
date: 2008-05-21
forum: General Help
---

### Post by ryanconnarton on 2008-05-21
Ubuntu Studio will not let me install any other operating system! This is a big problem for me, I figured out that Linux isn't the best choice for my laptop. I requested help in a different category on the Ubuntu forum but no one seemed to know. I stated in my previous thread:

I installed Ubuntu Studio on my Acer Aspire 4720Z and I can't get the wireless driver for the Atheros AR5BXB63 to work so I want to go back home to Windows. Its a darn shame too. Ubuntu Studio is the best operating system I've ever used (besides Mac OS X Leopard of course (- but for x86 arcitechture....it is supreme! Everything I need! But I want Windows back now. When I run my Acer restore system disk, it gets a little ways through the menus and starts to appear to be restoring and then out of nowhere it will just boot to Ubuntu Studio. So now I bought a copy of Windows XP and it wont boot from that disk AT ALL! it just boots right up to Ubuntu Studio even though the BIOS settings are configured to boot from my DVD-RW drive. How can I fix this problem?

Thanx for the help guys.

---

### Post by Ericyzfr1 on 2008-05-21
Did you try to install ubuntu? I never had any problem installing anything over Ubuntu. Or you need an app to wipe your HD clean.

---

### Post by johnwillis on 2008-05-21
You need to delete all your linux partitions first, then your factory restore disc will pick up the hard drive correctly.

You have several options:

Use the linux live CD again and install a tool (over ethernet) called "GParted" using Synaptic and delete all the partitions on your hard disc.

Use a boot CD such as Herin's (not quite so legal ;P)

Or use a OEM/Legal version of Windows that can use the Windows partitioning tools.

In my opinion the first is the easiest.

Hope this helps.

-J

---

### Post by jakupl on 2008-05-21
I'm guessing he can't do the first option as there is no live cd for ubuntu studio.

only alternate.

you could make a live cd of gparted and use that instead.

---

### Post by johnwillis on 2008-05-21
Alternatively he could use any Live CD version of Hardy/Gutsy or even Edgy!

It really won't matter so long as you have the partitioning tools.

You could even use FDISK off a Windows 98 boot CD/floppy if you wanted. But I'll be honest you just need to boot off a Live CD then run the following:

```
apt-get install gparted
```

Say yes to everything and your good to go. Just type "gparted" into the run command and erase all the partitions and like I said before your restore disc should be fine restoring.

Chances are the Acer disc cannot read EXT3 partitions and therefore believes there is no hard drive.

-J

---

