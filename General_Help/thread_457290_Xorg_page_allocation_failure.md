---
title: "Xorg: page allocation failure??"
date: 2007-05-28
forum: General Help
---

### Post by Protoss on 2007-05-28
Today when I booted into Feisty, I try to start uTorrent, and it looks to start, but nothing happens, and I have to kill wine and utorrent.exe. I do a "dmesg|tail" and find > Xorg: page allocation failure along with some really cryptic numbers. I had some problem like this a month ago, where uTorrent refused to start, or any wine app, and the only solution was to reinstall...but now  the problem is back. I've uninstalled wine, reinstalled it from the reps, but still nothing. 
I am now booted into XP, and uTorrent is working fine (I share the utorrent folder+all its .dat files between XP and Feisty) so its definately a Feisty problem. 
I've tested my RAM, and it was perfect. 
Anyone got any ideas?

---

### Post by yopnono on 2007-05-28
> **Protoss said:**
> Today when I booted into Feisty, I try to start uTorrent, and it looks to start, but nothing happens, and I have to kill wine and utorrent.exe. I do a "dmesg|tail" and find  along with some really cryptic numbers. I had some problem like this a month ago, where uTorrent refused to start, or any wine app, and the only solution was to reinstall...but now  the problem is back. I've uninstalled wine, reinstalled it from the reps, but still nothing. 
I am now booted into XP, and uTorrent is working fine (I share the utorrent folder+all its .dat files between XP and Feisty) so its definately a Feisty problem. 
I've tested my RAM, and it was perfect. 
Anyone got any ideas?

Only to let you know... utorrent are a windows program

---

### Post by Protoss on 2007-05-28
> **yopnono said:**
> Only to let you know... utorrent are a windows program
Yeah..I know this. Thats why I run it thru Wine.
Oh and [this]("https://bugs.launchpad.net/linux/+bug/109177") is the problem I was having. I just booted into the live cd and ran > fsck.ext3 -fcy /dev/sda3 and it fixed some HTree errors, which I guess were the problem. 
Seems like ext2ifs is corrupting some part of the partition.

---

