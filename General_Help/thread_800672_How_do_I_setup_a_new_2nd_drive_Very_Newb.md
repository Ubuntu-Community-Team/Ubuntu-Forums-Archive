---
title: "How do I setup a new 2nd drive? Very Newb"
date: 2008-05-20
forum: General Help
---

### Post by Return Privacy on 2008-05-20
Hi all,
I am VERY new to linux. Installed ubuntu 7.10 on a 40gb drive connected directly to the motherboard. Now, I put in a 3Ware 9500S-8 raid card with drives attached to it. I created a raid 5 array in the 3ware bios during boot up. Now, I just need to know how to setup the new raid drive in Ubuntu? I did install gparted. I don't know how to use it? I just need to setup this new raid drive as one drive, one big partition, I think ext3? is what I should use for file system? All this machine will be doing is acting as a place to store files for my home network. I have a mac OSX computer and a pc (xp) on the network. My new ubuntu computer is online( can access web) connected by ethernet to the same router as the other two computers. I just need someone to help me get this new drive setup and seen in the ubuntu OS. And, I guess the next question would be how to see that new drive from the mac and xp machines?
Thank you very much in advance for all your help!

---

### Post by lynxus on 2008-05-20
have you tried creating the partition with gparted?

maybe:
foo@bar$sudo gparted

Or somewhere in the gnome menus will be a partition program.. System -> Admin maybe?

---

### Post by Return Privacy on 2008-05-20
Hi,
Yes, I just opened gparted. It shows the /dev/hda 40gb hard drive that has the OS, and /dev/sda. The /dev/sda says it has -199071099392.00 B, not GB? when I hit information for that, it shows it as the 3Ware controller card? Is this the new raid drive? When I go to create a new partition, it shows as 0 space ?

---

### Post by fjgaude on 2008-05-20
From my experience, gparted doesn't handle raid at all... it sees a piece of the array and that's it. You can't format, i.e., install a filesytem on raid array using it.

There are command line tools to do this. One is fdisk and cfdisk. The latter is somewhat graphical. But first...

... has Ubuntu recognized the array as a /dev/<something> device? I guess so. Then have you installed the necessary driver software for the 3ware card? Okay, do this and report back:

```
sudo cfdisk /dev/sda
```

---

