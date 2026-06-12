---
title: "Wanting to setup a Software Raid 5"
date: 2007-01-02
forum: General Help
---

### Post by Sqweeks on 2007-01-02
Well im looking to build a fileserver and dont care to spend alot on hardware raid cards. Going to have 4 500GB SATAII drives. Was thinking about doing a Raid 50 so I can just have a 1.5TB drive. Is it possible to do Raid 50 with software? And if so is there anyway you would be able to add more drives to that array to make the size larger?

What i want to do in the end is have at the start a 1.5TB folder were I can have all my videos (Movies, Shows, Anime, etc..) 

I have over 1TB in external drives right now and want all of my files to have some what of a redundancy but do not want to have to have 2 Movies folders once i fill up the 1.5TB's (plan on adding a 500GB drive every 3 months). Dont expect to much traffic on the fileserver, just stream videos and music off it for my HTPC.

Plan on using a  PROMISE SATA300 TX4 PCI SATA II 4-Port Adapter, Would a controller card on a normal PCI slot be fast enough or should I get a PCI-X one? Dont plan on having much bandwidth on the server, only about 2 computers will be using it to store files and stream video.

If I do end up having to use 2x 4 port Raid cards is there anyway i can have one folder display whats in both drives? so say if i had one 1.5TB drive then another 1.5TB drive and each one had a Movies folder in it. Would i in anyway be able to have both Movies folders display the contents in another folder?

System:
P4 Prescott 3.2 GHz
2GB PC3200 DDR
40GB PATA for OS
4x 500GB SATAII

I am some what of a noob to Linux, Ill mess with it on and off but never tried making a file server before.

---

### Post by ingo on 2007-01-03
Wow, that's a lot of questions! You gotten anywhere with any of them? A Raid 5 is supposed to be quite simple provided you use the alternative cd (without the graphical installer). I've also seen a few decent (i.e. understandable) howtos with plenty of screenshots that should answer all your questions, but unfortunately cannot remember where :(

---

### Post by jpkotta on 2007-01-03
Here is a good one about RAID1, I'm hope it applies to RAID5 as well.  I'm going to build a file server as soon as I decide on the HDDs and controller, and I was planning on using this guide.  There are other RAID howtos in the wiki (hint: use the search).

[https://help.ubuntu.com/community/FileServerOnLVMOnRAID1](https://help.ubuntu.com/community/FileServerOnLVMOnRAID1)

---

### Post by jpkotta on 2007-01-03
I think you need at least 3 devices for a RAID 5 setup.  I don't see how you can do RAID 50 with only 4 drives.  Why not make a RAID 5 array of all 4 drives?

After looking through the LVM howto and Software RAID howto (linked in the article I posted), I think what you want is [this]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO-11.html#ss11.2"):

```
VG
|
|--RAID5
|   |
|   |--disk1
|   |--disk2
|   |--disk3
|   |--disk4
|
|--RAID5
    |
    |--disk5
    |--disk6
    |--disk7
```

This is a volume group composed of 2 RAID 5 arrays, each array in turn is composed of 3 or 4 disks.  You need at least 3 disks for a RAID 5 array, and those disks should be the same size.  LVM doesn't care if the RAID arrays are the same size or not, and it is easy to add physical devices (either disks or arrays) to the volume group.  

You want to add disks in the future, and from what I've read, it seems [hard]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO-10.html#ss10.1") to expand arrays but [easy]("http://www.tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html") to expand volume groups.  On the other hand, it's a pain to add 3 disks at a time.

I think this setup is what I'm going to do.

---

