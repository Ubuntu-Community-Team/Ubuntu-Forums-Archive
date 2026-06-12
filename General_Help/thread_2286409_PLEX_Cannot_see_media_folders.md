---
title: "PLEX Cannot see media folders"
date: 2015-07-11
forum: General Help
---

### Post by Steve_Cline on 2015-07-11
I am running 14.04 and just installed PLEX.  I have not been able to find the folder that contains my media.  After reading through many forum threads and trying some of those solutions I am thinking I need to put up my specific details to get this solved.  I am fairly new to Ubuntu so please talk to me in small words;).

My system has two external drives which both have a "Media" folder in them containing movies (and eventually TV shows and Music once this is working).  The first is a 2TB SSD with NTFS file system.  I added PLEX to the plugdev group.  When I tried to change permission on the SSD I could not change plugdev permissions through Nautilus So I copied the media folder to the other drive (which I first formatted to Ext4).  Then I gave plugdev permission to "Create and delete files" on that drive but I still cannot get PLEX to find them.  When I try to edit my library from the PLEX Media Manager I can find the drives but not any of the subfolders.

Any suggestions are appreciated.

---

### Post by TheFu on 2015-07-12
You need to "mount" the storage with appropriate permissions for plex to see it.  Linux is a multi-user OS and so many different userids are on the system. Plex Server uses the "plex" userid.  That userid must be able to "read" the media files.  

I wouldn't waste time with plugdev.

With linux file systems - that means just making normal file permissions sufficient for the plex account to read.
With NTFS it is a little harder because NTFS permissions don't translate to Linux.
Oh - and you'll need to use the plex web interface to tell plex where the new disks are.

So ... there are 1000000000 different ways to do this. The way I do it with plex is to mount media storage until /D/ **sudo mkdir /D**.
A "mount point" is needed for each partition. A mount point is just an empty directory - I don't call them folders.  So **mkdir /D/TV /D/Music**

A little script to mount my portable media off an NTFS partition. My userid is 1000 and the gid is 1000. You can find yours with the **id** command.```

#!/bin/bash
UID=1000
GID=1000
LABEL1=TV
LABEL2=Music

sudo mkdir -p /D/$LABEL1 /D/$LABEL2
sudo mount -t ntfs -o uid=$UID,gid=$GID LABEL=$LABEL1 /D/$LABEL1
sudo mount -t ntfs -o uid=$UID,gid=$GID LABEL=$LABEL2 /D/$LABEL2
```
I don't let plex access the NTFS storage, it is just for copying over in my environment. For plex to see it, I'd need to set the permissions mask for files and directories. Don't know those off the top of my head for NTFS - the manpage for mount.ntfs should have that info.  fmask and dmask loot to be it.  So where the mount options go, fmask=002,dmask=002.  The manpage here says full access to everybody is the default - scary!  I didn't test the fmask stuff, but you can add that to the mount options, right?
-o uid=$UID,gid=$GID,fmask=002,dmask=002

For the Linux storage, just **sudo chmod -R  ug=rwX /D/TV; sudo chmod -R o=rX /D/TV;** - assuming TV is the Linux partition.
For the Linux partition(s), just drop the needed lines into the /etc/fstab. Use the UUID for that - though a label can be used too. If the NTFS partition isn't going to be removed, I'd mount it through the fstab too.  If you want to use plex to manage the media completely, you can just **sudo chown -R plex.plex /D/TV** - but your userid won't have much access then.

BTW - for streaming media, an expensive SSD just isn't needed in most uses.  I suppose if streaming to 50+ different users concurrently was needed, then an SSD would make sense. For typical home uses, a USB2 disk is more than fast enough for 1080p video content.

There are 1M ways to accomplish this.  A solid understanding of Unix file/directory permissions is needed. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) should help.

---

### Post by Steve_Cline on 2015-07-13
OK so I am going to tackle the linux part and see if I can get it working.  I may not bother with the NFTS drive.  That is my external hard drive that contains a lot of my GIS files anyway so I will just buy another HD if I need more space.

Let me make sure I understand this though.  If I use mkdir I create the mount points (folders) and then use chown to change the permissions to allow PLEX to manage the media.  In that case I would be able to access existing media in PLEX but my userid would not be able to make changes or add media.  Is that correct?

---

### Post by TheFu on 2015-07-14
Yes, unless you add your userid to the "plex" group and I would set the "setgid" permissions bit on the first directory made, then all will be fine and easy.  Learning about normal file and directory permissions is an important aspect of a Unix system. You need to understand this stuff. There are tutorials online - mostly at .edu websites.

---

