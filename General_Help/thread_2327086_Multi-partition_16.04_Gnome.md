---
title: "Multi-partition 16.04 Gnome"
date: 2016-06-07
forum: General Help
---

### Post by BikeRich on 2016-06-07
Hello to All :

  I'd like to install 16.04 Gnome with the following partitions :   /        /home      /usr     /var     /tmp   .

  Was told this arrangement will make the next fresh install to 16.10   easier ,  because all the settings, apps, etc  will be right there for the newer Ubuntu to see and use automatically .

  Two questions :  what size for each partition  (space is not a problem, but there are already 4 OSs on the 1 T disk , win 7,win 10, mint 17.2 and Unity , if that is relevant ) .

  Also , would anyone care to comment on the multi-partition-for-one-OS idea ?  Yes , I did search before posting this. Thanks for any comments/suggestions .

                                                                 
                                                                                                                                                                                bikerich

---

### Post by oldfred on 2016-06-07
Suggest only / (root) and swap which is the default for all new installs.
A bit more advanced is the separate /home.
Regular users do not need othe system folders as separate partitions as then you get into the size issues. And may depend on how you use system. And with just / if you need more space it is there as it all is shared. If separate partitions you have to do a lot of moving data & resizing partitions.

I also do not automatically suggest installing 16.10. While I will install 16.10 (actually already have), I keep a LTS version as my main working install and do not normally change that until the next LTS version comes out or 18.04. 

I normally use 25GB for / (root) but have all data in shared /mnt/data partition so every install has access to same data. Back when I still had XP I also had a shared NTFS data partition for that data I wanted in all systems including XP like my Firefox & Thunderbird profiles. And all the photos that I use Picasa (now obsolete) for in both XP & .wine.

---

### Post by Impavidus on 2016-06-07
Putting /home on a separate partition is often useful. /home contains all your personal settings (as opposed to system-wide settings, which are in /etc, which is always on the root partition) and your documents. The others may help a bit in case of an overflowing directory (some process flooding the logs or /tmp with useless messages of files), but that should rarely happen. I think that only in special circumstances creating separate partitions for /usr, /var and /tmp does any good.

FYI, I put everything except /home in one partition (and except /usr/local, but for most people that should be rather empty). My root partition contains about 10 GB, /usr is 8 GB, /var is 860 MB and /tmp is almost empty, but that may depend on what you do on your computer. You can use all remaining space, except what you want to reserve for future purposes, for /home. Make all your partitions a bit larger than what you need as minimum.

---

### Post by BikeRich on 2016-06-09
oldfred and Impavidus :

     Thank you both.   Oldfred , why  a /mnt/data partition  instead of /data ?  Also, is /mnt/data formatted the same as the other partions ? Great is my ignorance .


     As far as partition size , how about 25 Gb for /  and 10 Gb for all the others ?


                                                                                bikerich

---

### Post by oldfred on 2016-06-09
The default mount of external drives is /media/$USER.
But that shows in left panel of Nautilus. I leave partitions I do not use much or occasionally to mount in /media, but try to remember to label them so I easily tell what it is.

I have mounted in /, but then someone posted that was non-standard. As an individual user that was ok. 
But Linux standard base mentions both /mnt & /media as mount points.

My /mnt/data is ext4, when I still had XP years ago, I had a /mnt/shared that was NTFS. Some data went into each partition.
With ext4, I do have to set ownership & permissions (similar to defaults in /home) to let me use my data.
I link the data folders you normally see in /home like Photos, Documents, etc in my data partition.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by BikeRich on 2016-06-09
oldfred and Impavidus

      Thanks for your comments and info .  I'll have to work at understanding all of it !   If no more replies in a couple of days, I'll mark this thread solved.      bikerich

---

### Post by Impavidus on 2016-06-10
> **BikeRich said:**
> oldfred and Impavidus :

     Thank you both.   Oldfred , why  a /mnt/data partition  instead of /data ?  Also, is /mnt/data formatted the same as the other partions ? Great is my ignorance .


     As far as partition size , how about 25 Gb for /  and 10 Gb for all the others ?


                                                                                bikerich
I'd say, 2GB swap partition, but you can share that one with Mint and Ubuntu Unity, so no need to create it. If you want a separate /home partition, make / (the root partition) 15 to 25 GB, depending on how much you can spare. Unless you have a special reason to create them, don't create separate partitions for /usr, /var and /tmp. It won't make new installs easier. If you don't want a separate /home partition, just put everything in one big partition. With so many operating systems, a separate data partition (accessable from all systems) may be more useful than a /home partition.

If you really insist in separate partitions for /usr, /var and /tmp (not recommended), then make /usr 15 or 20 GB, the others about 5 GB.

---

### Post by BikeRich on 2016-06-11
Impavidus

      How to make " a separate data partition (accessable from all systems) "  ?  That I'd like to know how to do .


                                        bikerich

---

### Post by oldfred on 2016-06-11
See post #4

---

### Post by Impavidus on 2016-06-12
Create an extra NTFS partition with no OS installed. But you may already have one. Windows will recognise it as "drive D" or "drive E" or something like that. On Linux, you can mount it (attach it to the directory tree) using fstab. Use that to store all data you want available on all systems.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Don't forget to read oldfred's links too.

---

