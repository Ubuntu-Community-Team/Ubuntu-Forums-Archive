---
title: "Wubi CONVERTS report in!"
date: 2007-11-19
forum: General Help
---

### Post by ericesque on 2007-11-19
The Wubi team has done a wonderful job of creating a tool for users to get a feel for how Ubuntu will perform as a native install on their machine.  In almost every regard, Wubi creates a perfect emulation of a native install.  Yet Wubi is designed as an intermediary between a live cd and a native install. As Ago continually reminds us: if you like Wubi, it is wise to move to a native install.

This is exactly what I have done.  

After about three weeks of 7.10 via Wubi I knew Gutsy was on my machine to stay.  I was considering making the move to a native install for about a week-- but alas, intertia had kept me put.  
 The force that finally made me move was when I went to install BF2 in Wine and found that my home partition wasn't big enough.  With 7.10 LVPM support unaccounted for, I decided it was time.
 I stole 15GB from my XP install and an additional 20GB from a second 'media' partition.  This was my first time installing from a live cd instead of an alternative cd.  I have to say that the install was easier than Vista--and Vista is pretty darn easy! Importing settings, documents, and the wallpaper from my XP install: nice touch!
 A few hours later I'm settled into my new native install. Why is Ubuntu my choice of OS? It has beauty,functionality, and stability that mac and Vista can't begin to touch and a community of awesome people who are willing to help troubleshoot a problem or simply swap stories and ideas. What else is there to want?

Why did you convert your Wubi install to a full blown Ubuntu install? Share your thoughts-- your story!

---

### Post by daspooky on 2007-11-21
Hehe, I like this kind of topics :) I am currently running Feisty on Wubi 7.04 and believe me, if I could, I would format the whole damn computer and only run a complete Gutsy install :) (I have no need for Windows anymore).

Unfortunately we are not in a perfect world, and I'm using Ubuntu on my work laptop (not allowed to remove windows xp on this one :( ).. So I will have to stay with wubi for a while, as this is the closest I can get to a full install on this laptop.

Anyway, I'm curious to read other people's adventures :)

---

### Post by VanMuur on 2007-11-21
I have quite an adventure with Wubi. 

I don't have a second hard disk to put Linux on, and I also don't like partition for the sole purpose that most new laptop and desktop manufacturers give you a hard disk that has a recovery partition. This makes repartition the current drive a nightmare, as I don't want to delete the recovery partition, and some of the drives I have are small enough as it is, let alone taking a chunk out for Linux.

I also go through phases where sometimes I want the space for Linux and sometimes I want the space for Windows.. it all depends on what I'm doing at the time. Thus, since there is no LVM equivalent for Windows, I wanted to find some other way to run Linux without reformatting. (I guess I could just hunker down, buy a USB drive and install Linux to that.. but not all hardware I have can boot off of USB drives... I know, I know.. just get a newer computer.)

Anyways, I've been researching loop-rooted filesystems for a long time, trying to find just the answer when I ran into Wubi. It pretty much solved 90% of my problems. I was able to run Linux on a system without reformatting.

I often do very experimental things with my Linux, since I'm always into trying the bleeding-edge stuff. Right now, its Xen, since I know its up-and-coming in the commercial world. So, lately, I've been trying to get a Xen "enable" Wubi kernel going. I know most Ubuntu kernels work "out of the box" with Wubi installs, but the Xen compiled kernels don't seem to like the loop-rooted setup. Also, mkinitfs also doesn't like the loop-rooted filesystem, gets confused by it, and refuses to build initrd's (initramfs'). So, its pretty much put a damper on my work with that. (On a side note, I was able to get Xen working inside a VMware instance, but thats another story.)

So, all in all, I'm very happy with Wubi, but only as an end-user, not as a experimental user. Regardless, it does what it advertises: a great desktop on an NTFS backed filesystem.

---

### Post by open2linux on 2007-11-22
I am a happy Ubuntu user now and I have a regular install of Ubuntu 7.04 Feisty Fawn on its own partition. But I never would have gotten into Ubuntu without Wubi.

I have a laptop without CD driver, so Wubi was for some time my only chance. I have Windows XP, and with Wubi I installed Ubuntu and used it for several months. I quickly learned to do all my works in the Ubuntu side; word processing, web design, email, ...

Then I got the oportunity for a regular install when I borrowed a CD drive for a few days. I had the Ubuntu CD that I got from the "ship it" servive of Ubuntu, waiting for this oportunity, so I easilly created a partition for Ubuntu and installed it.

Still I check this site from time to time, to see when for Wubi 7.10 stable is out, so I will try it and recomend it to friends.

I am quite thanful to the Wubi developers for their work, and as a little retribution  I translated Wubi into Spanish. Happy to contribute a bit with this project. I never miss a chance to recomend Wubi to anybody I find interested in Linux but afraid of partitions.

I do hope Wubi will come included in Ubuntu 8.04 . Being LTS it will be probably more widelly used than previous versions, and Wubi could  make it even more friendly to try.

---

