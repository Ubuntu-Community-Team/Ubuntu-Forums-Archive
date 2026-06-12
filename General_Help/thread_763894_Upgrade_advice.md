---
title: "Upgrade advice"
date: 2008-04-23
forum: General Help
---

### Post by peakshysteria on 2008-04-23
Currently I'm running a dual boot with XP X64 Pro and Hardy Heron. Due to some issues with my XP and some heavy problems with my ATI card on Hardy I've decided to make a clean install of both Windows and Hardy Heron.

My current setup:

Three discs split into four (five) partitions like this: HDD 1: C,D (+Ubuntu aprox 40 GB) HDD 2 E and HDD 3 F.

I'll take a backup of all files to an external HDD. Then i want to reinstall both OS's. Last time i installed windows then installed Ubuntu on the free space. Every partition is reachable from Ubuntu. But the Ubuntu partition is not reachable from XP now. In time, and if my ATI card plays nice, i want to make the complete switch to Ubuntu.

I'm not sure this is the right thing to to right now since ATI is poorly supported. And I'm in bad need of both tv-out and overlay.

Is there anyone out there who can recommend the best way to reinstall the two OS's? I'd also like to here recommendations on an alternative setup (if there is a point to it).

And i'm getting a new external HDD of aprox 750 GB. Is there a point in splitting this up into more than one partition? Or is it recommended to have only one partition? (this is meant to be a backup disc only).

---

### Post by markharding557 on 2008-05-05
the way you set it up before is correct
don't see any point in splitting your other drive up unless you have a reason to do so.
also try some different live cds out to see how they perform on your hardware

---

### Post by peakshysteria on 2008-05-06
Thanks man. It all went pretty smooth actually. But I made a mistake when choosing the which partitioning to use from the live dvd. So Hardy got installed on the first HDD. The to other drives are still respectively NTFS and Fat32. I can read from both, but one of them i can't write to. I was hoping to get a complete Ubuntu across the three HDDs. So now I have to bring out some partitioning program like Gparted or something :( Never used it before so I'm kinda in the wild here :)

---

### Post by markharding557 on 2008-05-06
gparted is easey to use it is a bit like partition magic on windows.
shall i assume you have no windows now?in which case you can format the others to ext3.
if you want write access to ntfs you need package ntfs-3g installed,fat32 has been read/writable for some time

---

### Post by peakshysteria on 2008-05-06
But i can use Gparted from within my excisting Ubuntu right? I don't need to use the live cd?

And yes, your right, now there is windows no more (at least not for a while). But my Ati card is killing me. Can't get Compiz up and running anymore and can't get my beloved tv out with overlay. Can't get tv out at all actually. That'll be the project for the summer anyway. And java is a problem. Can't seem to get my bank to handle my java.

Everything is slowly coming along. Most things are running very smooth :) Gparted and partitioning the to remaining drives is the next big step. Or should i just leave them alone? What's the advantages in partioning the two remaining drives into ext3?

And can you recommend a backup tool? Something safe, easy and intuitive... :)

---

### Post by markharding557 on 2008-05-09
i have read that 64bit systems can be tricky to set up with java and flash,i don't know much about this with running an athlon but others on the forum do.
post a separate thread for your ati card because it is a fair bet others have had and probably resolved simlar issues.
good luck

---

