---
title: "Buffering...buffering...buffering.......VLC,  XBMC"
date: 2013-10-07
forum: General Help
---

### Post by Kymus on 2013-10-07
Lately I've had major issues with video buffering and it seems like it doesn't matter what medium I am using to play the files (XBMC or VLC). This morning I got fed up with this, so I decided to just start counting. Every 30 seconds to a minute it will stop and start buffering. Sometimes it's less than that and even between 7 and 15 seconds.

Case 1:
720p
H264
2-channel audio
Dolby

Case 2:
720p
H264
5.1 audio
Dolby

Case 3:
720p
AVC
2-channel audio
AAC

I checked my system monitor while this was playing; both in VLC and XBMC. System ram was never above 30% and CPU was never really above 20% across 4 cores. Aside from system stuff in the background, the only extras running were dropbox (not syncing) and UbuntuOne (also not syncing). Ok, SABnzbd (nothing downloading) and Sickbearbeard were running in the background.

It just doesn't seem right to me that this much buffering is going on for my system. I'm running a fresh install of Ubuntu (maybe 2 weeks old or so). I've used the exact same hardware (well, minus 4GB RAM (see below)) before I had to format (someone's script borked my system) for the past year and I've never experienced this issue. I'm puzzled as to why this is going on. 

Here's what I'm working with:
Ubuntu 13.04
ASUS F1A75-I Deluxe FM1 AMD A75
AMD A8-3850 Llano 2.9GHz Socket FM1 Quad-Core (with DirectX 11 Graphic AMD Radeon HD)
G.SKILL Ripjaws X Series 8GB (1 x 4GB)(RAM in my PC went bad, so I've got the two sticks spread between my PC and HTPC until I get a remplacement) 

I've also got screenshots available of my system monitor while buffering was going on, if that's helpful.

---

### Post by Kymus on 2013-10-07
I'm starting to wonder if it's the disk. 

I house my media on two external WD elements drives.

Movies on one, TV and Anime on the other.

These drives have a FAT32 or NTFS file system (not sure which) and they've never been defragged, ever. One is 2TB and the other is 3TB and they're both about 500GB (or less) shy of being full.

I noticed that media I've played that's housed on the second drive I have had little to no issue with, and the same goes for media played from my internal drive. I'm transferring a file that has played well on my internal drive to the external drive with movies and the speed is getting slower and slower. It's a 675mb file and the drive is plugged in to a USB 3.0 slot and the speed is down to 365k/sec. 

I'm thinking that the drive is fragged to hell and needs some serious work..

---

### Post by Kymus on 2013-10-07
Auslogic says the disk is only 16% fragmented. Not sure what to think now.

---

