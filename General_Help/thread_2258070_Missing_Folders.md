---
title: "Missing Folders"
date: 2014-12-24
forum: General Help
---

### Post by Groover20 on 2014-12-24
I am hoping that someone will be able to assist me with my current issue.

I have an old server running Ubuntu,on which I have 2 hard-drive containing Movies, TV Shows, Personnal Stuff, Pictures and Music.  A few weeks ago, I decided to upgrade it to 14.10.  I must add that after the upgrade the mounting path got modified.  It used to be /media/multimedia and /media/media  and it got changed to /media/server/media/multimedia &/media/server/media/media.

Yesterday, since the server was sluggish and that path were not working, I decided to re-install Ubuntu 13.04. 

This morning, while finalizing Christmas Gifts, I wanted to print a picture of our cat for the youngest one.  We had to put the cat down earlier this fall, and she has been asking for a picture ever since.  Unfortunately, I noticed that the Picture folder, along with the Music folder were gone.  I tried CTRL+H, search for *.JPG and *.OGG on the drives, but it didn't produce any results.

I checked using GPARTED, and it shows that the 1Tb drive is at 92%.  BUT, the Disk Usage Analyzer shows it at only 48%.  How do I go about retrieving the missing files/folders?  I mean, I don't really care for the MUSIC one, but I would really like to be able to get the pictures back.

Here are printscreens of GARTED and Disk Usage Analyzer

[ATTACH=CONFIG]258767[/ATTACH][ATTACH=CONFIG]258768[/ATTACH]

Thanks in advance for your help,

Groover

---

### Post by Impavidus on 2014-12-24
First of all, 13.04 is end of life. Your best bet to get a long term stable system is using 14.04 LTS, which has 5 years of support, whereas the others only have 9 months.

Let's get those mount points straight. You say you mount the partitions (one partition each on two drives) at
/media/server/media/media
/media/server/media/multimedia
Those names may be a bit confusing, but that's not the point (although it may be related).

The partition with 850GB of media files is however mounted at /media/server/media, as gparted shows, not at /media/server/media/media. Disk usage analiser shows there is 450 GB in the multimedia directory, which is supposed to be inside the /media/server/media directory, on which you mounted the other media partition. From the presence of a lost+found directory, I get the impression that /media/server/media/multimedia is a mounted partition too, which means that one media partition has been mounted on top of a directory in the other one. This could be the result of confusing names. But any files in the multimedia directory of the partition mounted at /media/server/media will be hidden by the other partition mounted on top of it.

So, double check the mount points of both of your media partitions. File on one partition may be hiding under the other partition.

---

