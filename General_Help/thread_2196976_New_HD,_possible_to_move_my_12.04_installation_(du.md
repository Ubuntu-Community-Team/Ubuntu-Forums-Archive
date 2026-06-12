---
title: "New HD, possible to move my 12.04 installation? (dual boot)"
date: 2014-01-01
forum: General Help
---

### Post by 777funk on 2014-01-01
I have a Win XP / Ubuntu 12.04 dual boot and I'd like to move Ubuntu to another drive. Is there a way to do this as if nothing ever happened?

---

### Post by oldfred on 2014-01-01
Will you keep both drives connected?

Do you have separate /home? Your user configurations and data are in /home.

So I usually suggest a new install. You then get a auto houseclean, and just need to copy /home over to new drive and mount it as part of new install. You can also extract list of installed apps and reinstall or if not housecleaned in old install can often copy the downloaded .debs. Only if you edited system wide settings would you need some of those from /etc.

If you do a image copy with clonezilla or similar application, you may have duplicate UUIDs. Only if not keeping old drive will it work easily. So then you have to change all UUIDs, manually update fstab, and reinstall grub. A few other settings may also be required to avoid issues.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

My backup is to be able to do a clean install. So this discusses what to backup. (or copy in your case).

 Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541

[/URL] To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

[URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

---

### Post by 777funk on 2014-01-01
The sad part would be that I have used this for a couple years now and have everything setup (keyboard shortcuts etc) how I like it. It'd be nice to keep all that in place if it were possible.

---

### Post by oldfred on 2014-01-01
I would think all that is in /home. If keyboard it may be in /etc.

---

### Post by 777funk on 2014-01-01
thanks oldfred, how would I preserve that? Is it a matter of copying a folder or two?

---

### Post by oldfred on 2014-01-01
I would partition new drive as you may want it but with a separate /home partition. Then copy your old /home to the new /home following the instructions in the link in my first post on moving /home. You just do not have to do the last part to erase the copy in your install on the old drive and mount in old install.
Then using manual install, include the mounting of your /home on your new drive but DO NOT check the format box. That should keep all your old /home data & settings in new install. If anything seems missing you still have old install on old drive to go back and find.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

