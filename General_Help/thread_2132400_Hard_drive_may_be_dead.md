---
title: "Hard drive may be dead"
date: 2013-04-04
forum: General Help
---

### Post by CyrodiilSavior on 2013-04-04
My friend recently has been having strange issues with his hard drive after installing ubuntu. The os completely freezes after loging in and you can't do anything about it except turn the computer off by the button. Upon trying to install windows back on the computer (just thinking ubuntu dosnt like his hardware) we found that windows couldnt install it's self on the drive. Now realizing it is a drive issue I decided to do further investigation. I put the drive into my ubuntu computer and planned to just format it and everything would be fine, I was wrong. The drive shows up in nautilus but I cant mount it, in GParted the main problem I see is that there is no partition table. when I try to create a partition table I am prompted with this message: > Input/output error during read on /dev/sdb After reading on the internet a little I have become very concerned. I have done multiple thing to fix it with no results. Help please this drive is brand-new and I'm afraid it might be dead.

Thx for the help.

---

### Post by Paulgirardin on 2013-04-04
in Ubuntu type "disks" in the dash and open the app.
If the disk is listed in red on the left panel there are errors.
 You can click on the 'more actions' button at the top right choose 'SMART Data and Tests' for more info and to run tests.

---

### Post by CyrodiilSavior on 2013-04-05
Thanks for the reply I checked on the disks app and it says there is nothing wrong with it. what would you recommend doing next?

---

### Post by deadflowr on 2013-04-05
Do know anything about the drive?

Stuff like name and type.(seagate,  or wd? sata, ide?)

---

### Post by mörgæs on 2013-04-05
> **CyrodiilSavior said:**
> this drive is brand-new and I'm afraid it might be dead.


Why not just get it fixed under warranty?

---

### Post by CyrodiilSavior on 2013-04-05
> [COLOR=#000000]Why not just get it fixed under warranty?[/COLOR] That is probably what im gunna end up doing I just figured it would be easier to fix it. (Apperently I was wrong)

As for the drive itself it is a WD 1tb

---

