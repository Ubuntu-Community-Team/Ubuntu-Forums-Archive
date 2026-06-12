---
title: "Kinda urgent!"
date: 2020-03-14
forum: General Help
---

### Post by xcfstarflight1 on 2020-03-14
Hi guys - System Backup PLan!
I really need to back up my system as is. The best way? I do have one SSD connected to the USB, I do have other disks. I have DVD roms i can burn to.
I need a system image i guess that i easily can recover from media. 
Thank you community for beeing there!

---

### Post by xcfstarflight1 on 2020-03-14
The only thing i get is to back up as a tar archive (this is tape archive right and gzipped?) sounds like a backup of my files but will this include ALL preferences and changes to /etc files etc.? Can i restore it from bootable disk?? Please I need to backup my system asap.
I know you guys work hard on helping out. I am in desperate need.

---

### Post by xcfstarflight1 on 2020-03-14
Just did a tape archive of / but I would like to make a recovery CD. Thou i guess the recovery option for this works. Just don't want to use too many 3rd party tools kinda like to learn the system :)

---

### Post by crip720 on 2020-03-14
You want a backup of just /, the whole system or just data?  The whole system containing everything will need another drive of the same or bigger size, Clonezilla or the dd command probably best for complete system or just root.  Ubuntu has dejadup installed for regular backups, there are others also.

---

### Post by Artim on 2020-03-14
Although rumor has it that this app is no longer supported, it works great on Xubu 18.04:  It's called SystemBack and it's point-and-click simple!  Get it [here]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10").

---

### Post by HermanAB on 2020-03-14
Well, any backup is better than no backup, but backing up Linux, is kinda pointless, since there are thousands of copies of it at Universities and ISPs all around the world already.

If you want to backup your data, then consider a versioned backup, which doesn't cost significantly more than a single backup:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by TheFu on 2020-03-14
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)

There are hundreds of different techniques. Each is about trade-offs.  Speed, storage, completeness, versioning, restore time, complexity.  Only you can decide what is important and the priority for each other consideration.

[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501) 
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)

Tar is a terrible tool for backups today.  Think of TAR as zip.  Would you backup an entire system using ZiP?  tar was designed when 250MB was huge.  There are many better backup tools.

---

### Post by GhX6GZMB on 2020-03-14
Timeshift will do a backup/restore of your system, including all configurations. Media is unimportant, but I suggest a USB stick.
It will **not** save your /home or /root documents, you'll need to this separately!

Install Timeshift, it's in your repo.

Before doing the backup, select "settings -> Users -> Include Hidden" for all users.

Then go ahead.

Cheers.

---

### Post by aljames2 on 2020-03-15
Like others have said, many options depending on your setup, needs, partitions & file systems.

Hopefully you will develop a backup strategy that runs regularly and test the restore process to make sure it works.

I am not a fan of “system image” backup schemes.  This implies a thought process of “...when my SSD/HDD craps out, I’ll just restore/recover to a new drive and life is good”.  Restores of system images are almost never identical and you end up with a “somewhat” restored system that can be buggy, can contain the same mixed up config that led to the crisis, and a pain that’s not worth it IMHO.  I prefer versioned backups of /home, /etc, /usr/local, and package lists.  Then recovery for me is a 10-minute fresh install, then install manual packages, then pull in from a backup my /home, custom configs & scripts.

Whatever you come up with, test it out to prove you have a viable backup & restore solution.

---

### Post by u666sa on 2020-03-15
Do you only have?
[COLOR=#b22222]Documents
Videos
Music
Pictures
Downloads[/COLOR]

If so and if size is less than 20GB total, then I would suggest [MEGA]("https://ubuntuforums.org/mega.nz/"), just type MEGA in google.

You install it and configure (option to the right during install) each folder you want to sync. And it automatically syncs all the folders you configure.  It's free, if the size is small. 

[URL="https://imgur.com/AjHvSsh.png"]
  [IMG]https://imgur.com/AjHvSsh.png[/IMG][/URL]

Added benefit, is that you can sync same folders on different PCs, thus your desktop is automatically synced across PCs.  Good practice is not sync Download, Desktop, and if you have it, DEV folders.

---

### Post by TheFu on 2020-03-15
> **aljames2 said:**
> Like others have said, many options depending on your setup, needs, partitions & file systems.

Hopefully you will develop a backup strategy that runs regularly and test the restore process to make sure it works.

I am not a fan of “system image” backup schemes.  This implies a thought process of “...when my SSD/HDD craps out, I’ll just restore/recover to a new drive and life is good”.  Restores of system images are almost never identical and you end up with a “somewhat” restored system that can be buggy, can contain the same mixed up config that led to the crisis, and a pain that’s not worth it IMHO.  I prefer versioned backups of /home, /etc, /usr/local, and package lists.  Then recovery for me is a 10-minute fresh install, then install manual packages, then pull in from a backup my /home, custom configs & scripts.

Whatever you come up with, test it out to prove you have a viable backup & restore solution.

May want to swap the restore order around a little.  During package installation, it looks for existing settings and configures according to those.  Basically, the re-re-install of manually installed packages should probably be the last step.  I do something like this across about 15 systems. Works very well. A restore takes 30-45 minutes clock time and about 10 minutes of human time.  Backups are usually 2-4 minutes per system after the 1st full backup gets created.
A few examples from last night:
```
=== Time for Backups to hadar === 
StartTime 1584250505.00 (Sun Mar 15 01:35:05 2020)
EndTime 1584250526.32 (Sun Mar 15 01:35:26 2020)
ElapsedTime 21.32 (**21.32 seconds**)
TotalDestinationSizeChange -214673 (-210 KB)


=== Time for Backups to romulus === 
StartTime 1584251108.00 (Sun Mar 15 01:45:08 2020)
EndTime 1584251248.85 (Sun Mar 15 01:47:28 2020)
ElapsedTime 140.85 (**2 minutes 20.85 seconds**)
TotalDestinationSizeChange 125092 (122 KB)


=== Time for Backups to nextcloud === 
StartTime 1584255014.00 (Sun Mar 15 02:50:14 2020)
EndTime 1584255292.37 (Sun Mar 15 02:54:52 2020)
ElapsedTime 278.37 (**4 minutes 38.37 seconds**)
TotalDestinationSizeChange 17066959 (16.3 MB)


=== Time for Backups to posc === 
StartTime 1584245224.00 (Sun Mar 15 00:07:04 2020)
EndTime 1584245673.15 (Sun Mar 15 00:14:33 2020)
ElapsedTime 449.15 (**7 minutes 29.15 seconds**)
TotalDestinationSizeChange 67880734 (64.7 MB)

```
Plus, not backing up the OS files, just the configurations, will usually save 4G of storage per system. For posc:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Mar 15 00:07:04 2020         20.2 GB           20.2 GB   (current mirror)
Sat Mar 14 00:07:04 2020         65.1 MB           20.3 GB
Fri Mar 13 00:07:04 2020         49.5 MB           20.3 GB
Thu Mar 12 00:07:04 2020         78.7 MB           20.4 GB
...
Thu Dec 19 00:07:04 2019         74.9 MB           27.8 GB
Wed Dec 18 00:07:04 2019          112 MB           27.9 GB
Tue Dec 17 00:07:04 2019         93.7 MB           28.0 GB
Mon Dec 16 00:07:04 2019          141 MB           28.1 GB

```
90 days of versioned backups - 20G backed up now, but only 8G more needed to have the other 89 days! Isn't that a bargain?!  Who won't agree this method is awesome?
Every Sunday morning, a script generates the same reports for most of the systems here.
```
inc-sizes-hadar-2020-03-15
inc-sizes-istar-2020-03-15
inc-sizes-romulus-2020-03-15
inc-sizes-lubuntu-2020-03-15
inc-sizes-nextcloud-2020-03-15
inc-sizes-spam3-2020-03-15
inc-sizes-xen41-2020-03-15
inc-sizes-zcs45-2020-03-15
inc-sizes-blog44-2020-03-15
inc-sizes-posc-2020-03-15
inc-sizes-vpn-2020-03-15
```

Here's one that should freak most people out, our email gateway server:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Mar 15 01:30:02 2020         63.1 MB           63.1 MB   (current mirror)
Sat Mar 14 01:30:03 2020         1.45 KB           63.1 MB
...
Thu Nov 21 01:01:03 2019       424 bytes           63.5 MB
Wed Nov 20 01:01:03 2019       906 bytes           63.5 MB
Tue Nov 19 12:43:18 2019         3.99 KB           63.5 MB
```
MB, not GB.  The backups are only system settings. There isn't any data. 120 days of versioned backups for a high-risk system.

Anyway, you've heard about people doing daily, versioned, backups and wondered how.  aljames2 does. I do. It really isn't any more complex than using rsync. The main command is almost the same as rsync would use, but provides so much more capability and flexibility than a simple mirror.  Hard-link based solutions have some faults. If you use one of those, hopefully, you won't be burned.  I've been burned.

Read an article somewhere that says Canonical is installing specialized kernels to support odd laptop motherboard+chipset devices.  If we restore an image, then those specialized kernels won't happen. Think it is for laptops only and a fairly recent effort by Canonical to provide the best possible support post-install. Don't know if desktops or servers are being handled similarly. Only laptops was mentioned in the article.

---

### Post by xcfstarflight1 on 2020-03-15
Thank you kindly for all your replies. 
I did the tape backup yesterday and copied it to an external drive.
When I was installing systembackup I needed to install two packages, duplicity and python-gi, then it automatically started but I am not sure how it works yet.

Things will sort them selves out :-)

---

### Post by xcfstarflight1 on 2020-03-15
OK doing a copy to an external drive once every week.

---

