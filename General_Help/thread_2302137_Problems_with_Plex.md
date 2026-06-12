---
title: "Problems with Plex"
date: 2015-11-07
forum: General Help
---

### Post by Chris_Fontanez on 2015-11-07
So I have an External HDD and I can read it on Linux no problem, but I can't see it when I try to add it as a Plex Media Server. Would i have to create that hardlink so my plexmediaserver can see my External HDD? Well it sees the HDD but none of the sub directories inside the HDD.

---

### Post by TheFu on 2015-11-07
PlexMS can have multiple directories for a single media type. It will merge that media together.  In the library management part of the web interface is a place to add multiple directories.

If the external HDD is always  mounted to the same place (which is easy to do) and the mount permissions  are correct so that plexms can read the files/directories, then it will work.

---

### Post by Chris_Fontanez on 2015-11-08
> **TheFu said:**
> PlexMS can have multiple directories for a single media type. It will merge that media together.  In the library management part of the web interface is a place to add multiple directories.

If the external HDD is always  mounted to the same place (which is easy to do) and the mount permissions  are correct so that plexms can read the files/directories, then it will work.

Thanks for the input, I know I kind of just bombarded the guys thread. The HDD is formatted for FAT32, but it still doesn't see any sub directories. I even opened permissions on the whole External HDD for testing purpose and still no. If I don't get a quick answer, I will create my own thread so I'm not taking over this guys thread.

---

### Post by Bucky Ball on 2015-11-08
*Post moved to own thread.*

Welcome.

[QUOTE=Chris_Fontanez]... I know I kind of just bombarded the guys thread.[/QUOTE]

Yes, you did. In future, please don't. Thanks.

---

### Post by Chris_Fontanez on 2015-11-08
> **Bucky Ball said:**
> *Post moved to own thread.*

Welcome.



Yes, you did. In future, please don't. Thanks.


Thanks Bucky wasn't really trying to take over, should of created my own thread in the first place. Thanks.

---

### Post by Bucky Ball on 2015-11-08
All good. :)

Sorry I can't help. I'm a Kodi man myself, which I think has significant difference to Plex. Probably an obvious question with an obvious answer, but the external hard drive is mounted and accessible from the desktop normally when you go to Plex and try?

---

### Post by Chris_Fontanez on 2015-11-08
Yeah the HDD can be fully viewed through Desktop and CLI, it's just only plexms not working. I use kodi as well. I have it on my phone, but sometimes those international (i say international because I'm in the US) is not very good as for quality wise. With plex I can get good quality streaming from wherever. But, back to subject, I will try to post some pics of screen shots of pretty much everything I'm seeing and show you guys what I mean.

---

### Post by Chris_Fontanez on 2015-11-08
Here are two screen shots, u can see in the background of the Term one, that I changed the permissions to 750, but I also changed them full priv for testing purposes. You can also see that in GUI and Term you can see the movies, no issue and I can play it from my HDD. But in the second picture you can't see the sub directories for PlexMS. My current fix right now is that I have a copy of the movies on the HDD of my computer and it can see those no issues. But I want to pull the movies from my external HDD as it is a bigger HDD space and it's partitioned for FAT32 so if I go somewhere I can use it on my Windows 10 laptop.

[[IMG]http://s8.postimg.org/pfd9aov5t/Ubuntu_Plex.jpg[/IMG]]("http://postimg.org/image/pfd9aov5t/")

[URL="http://postimg.org/image/44fp6fd1d/"][IMG]http://s8.postimg.org/44fp6fd1d/Ubuntu_Plex_1.jpg[/IMG]



[/URL]

---

### Post by Bucky Ball on 2015-11-08
[This any good?]("http://blog.tatedavies.com/2015/03/18/plex-external-fat32-usb-drive/") Perhaps Plex looks for mountable partitions in a particular spot. For instance, you seem to be mounting things in /media/mccrab. Can Plex look there? Have you tried mounting simply in /media, for instance /media/your_fat_partition (use the name of your partition, naturally. :))

Also, importantly, are you mounting the FAT drive at boot using an entry for it in the /etc/fstab file or you are booting then it is mounting wherever it chooses appropriate when you switch it on (or you are tweaking to mount it)?

As I say, I know little about Plex, but digging might throw up some more clues.

---

### Post by Chris_Fontanez on 2016-01-26
Hello guys, just an update I thought I would share this knowledge as I finally did get it to work.

The issue was that the user "plex" didn't have admin rights.  So what I did, was change the user of the plex-media-server to my user, and voila. I was now able to see all the subfolders in my external HDD and dump my movies on the external to use for streaming purposes over USB 3.0  I hope this can help anyone who is stuck, I also chown and chmod the External HDD.

---

### Post by Bucky Ball on 2016-01-27
Good news. It would help others more if you marked the thread as solved, please. See the first link in my signature for how. Good luck and thanks for sharing. ;)

---

### Post by Nuno_Abreu on 2016-01-27
It could also be a problem with the FAT32 partition because it does not support Linux links. I already had this issue in the past.

---

### Post by TheFu on 2016-01-28
> **Nuno_Abreu said:**
> It could also be a problem with the FAT32 partition because it does not support Linux links. I already had this issue in the past.

Hard links do not work across file system boundaries.
Soft links (really symbolic links) DO work from any Linux-based file system to any other, crossing file system boundaries and file system types.  It is possible to symlink from ext4 to NTFS, for example.  I don't know about FAT32 - let me test. Yep, that works too.  So it doesn't matter what the target is, just that the place storing the symlink is using a normal, Unix-style file system for symbolic links to work.  Of course, this means that symbolic links are stupid and can easily become stale and out-of-date.

I use Plex and Kodi daily.  Kodi is a play and Plex is the media server. Thanks to PlexBMC - an addon for Kodi - I get the best of both worlds.  Centralized DB management is great, plus the web interface for Plex is much better than Kodi.  OTOH, the plex company really wants their $4 for client apps.  I've never created a plex account or used any of their client-side apps for anything.  I did load some plex client on Android last week which was "free" ... well, it streamed for 1 minute.  60 seconds, then stopped with a message to pay $4 for the full app.  If they want money, fine. Have a paid app in the store. Don't waste my time with a "free" app that is really just trial. Left a strongly negative review for that.

Plex inside a subnet works fine without any plex accounts too. Just wanted to be clear on that. Sure, I wish they were F/LOSS, but the C/S parts are very nice.  Any DLNA client can use Plex.  On android, I like Bubble-something. It is a very powerful app - controls plex, kodi, and local playback. Can send media to any of those or other DLNA devices on the network.  I really need to pay them the $5 for the app. The app is definitely worth it for secondary control or when text entry is needed without being obnoxious.  Been using it for about 2 yrs, for free. However, a $17 cheapo remote is still the primary interface for Kodi/PlexBMC.

Plex storage and permissions.  This is really simple, provided there is an understanding that Linux is a multi-user OS and that different services (like plex), run as different userids.  The "plex" userid needs to have whatever access level required to do what you like with the storage. That could be read-only if you don't want Plex to be able to manage any of those files, or it could be read/write, if you'd like plex to be able to remove media - like for TV shows, I delete the media files through plexbmc. Very handy, IMHO.  For Music, I don't let plex have write/delete. Safer that way.  Many people deploy plex with limited Unix knowledge and they don't always understand normal, Unix file and directory permissions. We've all been there. That makes this issue come up all-the-time.  Plex isn't doing anything strange at all. It is behaving just like every other service and userid on the system.

Also - Plex doesn't have any hard-coded storage locations for media files.  Those can be placed anywhere. The web interface is used to setup storage for each library. It allows multiple storage locations to be added to each library section, so there isn't any need to use file system tricks like symbolic linking to get plex access to new storage.  I have multiple different disks - some are NFS mounted - connected to different media library locations.  /D/T, /D/T2, /D/T3 are where plex knows to find TV shows in my setup. Those locations were completely my choice.

Hope this clarifies things a little.

---

### Post by Nuno_Abreu on 2016-01-29
> **TheFu said:**
> Hard links do not work across file system boundaries.
Soft links (really symbolic links) DO work from any Linux-based file system to any other, crossing file system boundaries and file system types.  It is possible to symlink from ext4 to NTFS, for example.  I don't know about FAT32 - let me test. Yep, that works too.  So it doesn't matter what the target is, just that the place storing the symlink is using a normal, Unix-style file system for symbolic links to work.  Of course, this means that symbolic links are stupid and can easily become stale and out-of-date.

I use Plex and Kodi daily.  Kodi is a play and Plex is the media server. Thanks to PlexBMC - an addon for Kodi - I get the best of both worlds.  Centralized DB management is great, plus the web interface for Plex is much better than Kodi.  OTOH, the plex company really wants their $4 for client apps.  I've never created a plex account or used any of their client-side apps for anything.  I did load some plex client on Android last week which was "free" ... well, it streamed for 1 minute.  60 seconds, then stopped with a message to pay $4 for the full app.  If they want money, fine. Have a paid app in the store. Don't waste my time with a "free" app that is really just trial. Left a strongly negative review for that.

Plex inside a subnet works fine without any plex accounts too. Just wanted to be clear on that. Sure, I wish they were F/LOSS, but the C/S parts are very nice.  Any DLNA client can use Plex.  On android, I like Bubble-something. It is a very powerful app - controls plex, kodi, and local playback. Can send media to any of those or other DLNA devices on the network.  I really need to pay them the $5 for the app. The app is definitely worth it for secondary control or when text entry is needed without being obnoxious.  Been using it for about 2 yrs, for free. However, a $17 cheapo remote is still the primary interface for Kodi/PlexBMC.

Plex storage and permissions.  This is really simple, provided there is an understanding that Linux is a multi-user OS and that different services (like plex), run as different userids.  The "plex" userid needs to have whatever access level required to do what you like with the storage. That could be read-only if you don't want Plex to be able to manage any of those files, or it could be read/write, if you'd like plex to be able to remove media - like for TV shows, I delete the media files through plexbmc. Very handy, IMHO.  For Music, I don't let plex have write/delete. Safer that way.  Many people deploy plex with limited Unix knowledge and they don't always understand normal, Unix file and directory permissions. We've all been there. That makes this issue come up all-the-time.  Plex isn't doing anything strange at all. It is behaving just like every other service and userid on the system.

Also - Plex doesn't have any hard-coded storage locations for media files.  Those can be placed anywhere. The web interface is used to setup storage for each library. It allows multiple storage locations to be added to each library section, so there isn't any need to use file system tricks like symbolic linking to get plex access to new storage.  I have multiple different disks - some are NFS mounted - connected to different media library locations.  /D/T, /D/T2, /D/T3 are where plex knows to find TV shows in my setup. Those locations were completely my choice.

Hope this clarifies things a little.

Yes it did. I said this because these links are not cross-platform - I tried to had these between two NTFS filesystem and they did not work on Microsoft Windows.

---

### Post by TheFu on 2016-01-29
> **Nuno_Abreu said:**
> Yes it did. I said this because these links are not cross-platform - I tried to had these between two NTFS filesystem and they did not work on Microsoft Windows.

Windows has something "like" symbolic links, but it doesn't work everywhere. Check Windows-centric sites for info on that.

Why use NTFS on a Linux system anyway? I do everything to move data to Linux/POSIX standard file systems. Makes life so much easier, permissions are consistent and other good things work as expected, but Windows is the exception, not the default here.  If I need a file on Windows, I'll usually sftp it over using winscp. If ssh is setup, then sftp is setup. Convenient from anywhere in the world. That just doesn't happen too often. All media playback and storage happens on Linux-based systems here.

Oh - POSIX symbolic links ARE cross-platform - it is just Windows that doesn't understand them natively, since they don't talk Linux file systems natively. Linux, BSD, Solaris, AIX, HP-UX, Irix, OSF, DigitalUnix, Android and OSX all understand symbolic AND hard-links on POSIX storage.  So ... who isn't cross-platform?  If you use samba to share Linux storage with Windows systems, there are settings to allow symbolic links to be followed by Windows clients in the smb.conf file ... 
```
follow symlinks = yes
wide links = yes

```
Of course, these have security considerations, so they shouldn't be enabled without consideration to the undesired features; definitely NOT for samba shares where guests are allowed.

---

### Post by Nuno_Abreu on 2016-01-29
> **TheFu said:**
> Why use NTFS on a Linux system anyway? I do everything to move data to Linux/POSIX standard file systems. Makes life so much easier, permissions are consistent and other good things work as expected, but Windows is the exception, not the default here.  If I need a file on Windows, I'll usually sftp it over using winscp. If ssh is setup, then sftp is setup. Convenient from anywhere in the world. That just doesn't happen too often. All media playback and storage happens on Linux-based systems here.

Because unfortunately I need to use some flash drives on Windows and sometimes I need some shortcuts (the "links" on Windows) to have a fast approach in finding files in my filesystem mess - I wish everything was cross-platform... It's always possible to enable them (there's actually an ext4 driver for Windows, but I can't do this on every single computer I come across - and what about the administrator rights?).

> **TheFu said:**
> Oh - POSIX symbolic links ARE cross-platform - it is just Windows that doesn't understand them natively, since they don't talk Linux file systems natively. Linux, BSD, Solaris, AIX, HP-UX, Irix, OSF, DigitalUnix, Android and OSX all understand symbolic AND hard-links on POSIX storage.  So ... who isn't cross-platform?  If you use samba to share Linux storage with Windows systems, there are settings to allow symbolic links to be followed by Windows clients in the smb.conf file ... 
```
follow symlinks = yes
wide links = yes

```
Of course, these have security considerations, so they shouldn't be enabled without consideration to the undesired features; definitely NOT for samba shares where guests are allowed.
It's a great approach, yes - actually, I didn't know of it. I will try to play around with Samba sometime
Can this be applied to Linux RAID systems where you can't use them by default on Windows? I know you can use Windows RAID on Linux, but not the other way around.

---

### Post by TheFu on 2016-01-29
> **Nuno_Abreu said:**
> Because unfortunately I need to use some flash drives on Windows and sometimes I need some shortcuts (the "links" on Windows) to have a fast approach in finding files in my filesystem mess - I wish everything was cross-platform... It's always possible to enable them (there's actually an ext4 driver for Windows, but I can't do this on every single computer I come across - and what about the administrator rights?).

It's a great approach, yes - actually, I didn't know of it. I will try to play around with Samba sometime
Can this be applied to Linux RAID systems where you can't use them by default on Windows? I know you can use Windows RAID on Linux, but not the other way around.

We're talking about plex here. Do you move your plex storage to different systems?  That confuses me.  If your plex system is running Linux, then there isn't really any reason NOT to use Linux file systems for all the storage.  If you need sneaker-net storage to be NTFS, fine - $20 will get a huge USB3 HDD for that. Copy those files into the plex storage area and delete them from the sneaker-net storage.

RAID for Plex?  I never understand that in a home for stuff like media.  I use rsync to mirror media files to another set of disks a few times weekly.  RAID is only for "production" systems that must be available - i.e. HA.  Media doesn't have those requirements usually, especially at home. I have some RAID arrays for virtual machines, because if a disk failed under a running VM, "it would be bad."  If a media-holding disk fails, it really isn't that big of a deal. Swap in the mirrored disk and order a replacement.

---

### Post by Nuno_Abreu on 2016-01-29
> **TheFu said:**
> We're talking about plex here. Do you move your plex storage to different systems?  That confuses me.  If your plex system is running Linux, then there isn't really any reason NOT to use Linux file systems for all the storage.  If you need sneaker-net storage to be NTFS, fine - $20 will get a huge USB3 HDD for that. Copy those files into the plex storage area and delete them from the sneaker-net storage.

RAID for Plex?  I never understand that in a home for stuff like media.  I use rsync to mirror media files to another set of disks a few times weekly.  RAID is only for "production" systems that must be available - i.e. HA.  Media doesn't have those requirements usually, especially at home. I have some RAID arrays for virtual machines, because if a disk failed under a running VM, "it would be bad."  If a media-holding disk fails, it really isn't that big of a deal. Swap in the mirrored disk and order a replacement.

No, I don't need that - and I really don't use Plex anyway... I'm more of a Kodi person (the same applies, though).

I love rsync too! But having to type a command in the Terminal for every single transfer is bothersome... I know there is always the option of writing a simple script for it, but I know it will bottleneck my old computer (it's not that powerful, but it's great to watch some 720p movies, listening to my music, program and play some not-demanding games.
I use RAID because I already had problems with my data due to defective disks - that's why. And as I find RAID easier to manage than LVM, I gave it a shot and I have an array of it with almost 2.5 years. Running good so far.

---

