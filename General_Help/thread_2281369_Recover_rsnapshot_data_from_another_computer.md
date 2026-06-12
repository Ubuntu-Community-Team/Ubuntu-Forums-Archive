---
title: "Recover rsnapshot data from another computer"
date: 2015-06-06
forum: General Help
---

### Post by kapov on 2015-06-06
Hello my friends,

Here is a small setup I had, an old Dell PC with Ubuntu Server 14.10, two 3 TB hard drives, and a few softwares/applications.

The server had two purposes: a small web server and a network drive.

The first hard drive was used for all this, the second hard drive was 100% committed to backing up the home folder using rsnapshot.

Some time last week, the main hard drive failed, it seems to be a hardware failure as I tried many things and I can't get it to work, so reinstalling Ubuntu isn't an option. I'm not sure what I am going to do with the server, but I need to recover my backed up data. How would I do that using another computer? Right now I have two user folders and they cannot be accessed because I don't have the right permissions (using the live CD); I expect the same thing would happen should I connect the hard drive in my hackintosh (so I have both Win 7 and OS X 10.10 to try a recovery).

Any advice? I do not have an extra hard drive to install Ubuntu for the moment.

Thanks!

---

### Post by bab1 on 2015-06-06
> **kapov said:**
> Hello my friends,

Here is a small setup I had, an old Dell PC with Ubuntu Server 14.10, two 3 TB hard drives, and a few softwares/applications.

The server had two purposes: a small web server and a network drive.

The first hard drive was used for all this, the second hard drive was 100% committed to backing up the home folder using rsnapshot.

Some time last week, the main hard drive failed, it seems to be a hardware failure as I tried many things and I can't get it to work, so reinstalling Ubuntu isn't an option. I'm not sure what I am going to do with the server, but I need to recover my backed up data. How would I do that using another computer? Right now I have two user folders and they cannot be accessed because I don't have the right permissions (using the live CD); I expect the same thing would happen should I connect the hard drive in my hackintosh (so I have both Win 7 and OS X 10.10 to try a recovery).

Any advice? I do not have an extra hard drive to install Ubuntu for the moment.

Thanks!
I believe you can use OSX Fuse to mount the backup partition to your OSX 10.10 file system.  See [**here**]("https://osxfuse.github.io/") and [**here**]("http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/") for more info.

---

### Post by kapov on 2015-06-06
Thanks, I could successfully mount the drive on OS X with OS X Fuse and Fuse-EXT2 and the permissions issue is not even present. Now I have to deal with multiple "empty" files because rsync was not configured to make full copies... a few folders seem to be "consolidated" versions; others are not. We'll have to dig into multiple folders, still better than losing data.

Very glad I invested in a second hard drive for backing up! :p


Edit: well isn't that marvelous, I copied the latest backup and everything was there. A big A+ for rsync/rsnapshot!

---

### Post by bab1 on 2015-06-06
> **kapov said:**
> Thanks, I could successfully mount the drive on OS X with OS X Fuse and Fuse-EXT2 and the permissions issue is not even present. Now I have to deal with multiple "empty" files because rsync was not configured to make full copies... a few folders seem to be "consolidated" versions; others are not. We'll have to dig into multiple folders, still better than losing data.

Very glad I invested in a second hard drive for backing up! :p


Edit: well isn't that marvelous, I copied the latest backup and everything was there. A big A+ for rsync/rsnapshot!

My guess is that the '"consolidated" versions; others are not' issue is the** hard links** that rsync uses for differential backup of earlier versions.

---

