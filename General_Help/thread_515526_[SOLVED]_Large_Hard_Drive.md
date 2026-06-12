---
title: "[SOLVED] Large Hard Drive"
date: 2007-08-02
forum: General Help
---

### Post by MadMac on 2007-08-02
Howdy!

Okay, I just purchased a 320Gig SATA internal hard drive and I am wondering if anyone has any ideas on how to partition it.

It will have Ubuntu 7.04 installed and will also be used to transfer VHS to DVD.

I was thinking about letting Ubuntu take it all and then using Gparted to set up a partition just for the VHS input/DVD output.  Sounds pretty decent to me, anyway.

Currently, Ubuntu is happily residing on a internal 80Gig hard drive and Winders is happily residing on a separate 80Gig hard drive and I am dual booting (for now, anyway).  The main reason I dual boot is that I can't get Ubuntu to let me change the ink cartridges in my printer - but I am still looking and testing, just not there yet.

Anyone have any ideas?

Oh!  And if anyone has an idea for a program to read a VHS tape, store it on the hard drive and then copy it to DVD, I will be most appreciative!    :popcorn:

Thanks!

---

### Post by indytim on 2007-08-02
My recommendations:

1.  Use GPartedLive and pre-partition before installing the ops
2.  For your ops, you should reasonably need 5-10G max.
3.  Set up an ext3 partition for #2.
4.  Set up a /swap partition at ~2x RAM
5.  Set up a ext3 partition for /home (I'd use 5G)
6.  Set up an extended partition for the remaining space
7.  Set up whatever other partitions you need within the extended partition (use ext3) - ie backups, media etc.

Advisory : do each of the above or whatever variation one-at-a-time within GParted

Hope this helps.

btw - I've got a 160G SATA for ops and /home's and a 320 G for everything else.



IndyTim

---

### Post by sdowney717 on 2007-08-02
download virtualbox and virtualbox guestbox additions  from virtualbox.org

You can install XP in the virtual drive and it all works!, seemless integration between ubuntu and xp.

you can use this guide to help figure all this out. I went to virtualbox.org for the program deb for ubuntu. I have usb support and file sharing working.

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by MadMac on 2007-08-06
Thanks to both, but, for now, I have decided to use it mainly as a backup drive.  I will be using it for movie dubbing, in the near future, so it won't go to waste, that's for sure!

Thanks again!

---

