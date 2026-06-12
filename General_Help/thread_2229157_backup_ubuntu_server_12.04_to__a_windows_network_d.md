---
title: "backup ubuntu server 12.04 to  a windows network drive"
date: 2014-06-11
forum: General Help
---

### Post by mark103 on 2014-06-11
Hi everyone i've been looking around for a while now and said i'd come here to get a little bit of help,
i build an Ubuntu server a couple of months ago in RAID 1 two 3tb drives and have plex on it now everything is working brilliant thank god.

My plan is to backup the Ubuntu server i have with a 3tb drive i have installed in my custom PC now im looking for a push in the right direction on how to do this 
i just thought it would be better to backup my server from an external hdd just in case if the server went totally on me then i have it on my 3tb drive in my windows pc
any help would be really appreciated 

Cheers

Mark

---

### Post by TheFu on 2014-06-11
Linux backups need a Linux file system - or a self-contained backup archive format that retains file permissions, ownership, groups and any ACLs.  Windows file systems don't have that.  That means that you are stuck with the more complex backup methods for anything that isn't pure data like media files (video/audio files).

So - if you want to backup the system (and plex stuff) - I'd use 1 solution (posted about that a bunch here).
If you just want to backup the media files - pushing to NTFS will be fine.

Update - realized I didn't provide any tools:
* fsarchive if you want to clone partitions.
* rdiff-backup if you want to be highly efficient with storage, time, networking. Does differential backups with versioning. 10% more storage than a mirror, for 30 days of backups. 
* rsync for just the main media files - a clone.

---

### Post by mastablasta on 2014-06-12
to only root (programs and such ) a smaller disk would do. you can use Clonezilla or even Redobackup for that.

---

### Post by mark103 on 2014-06-12
ok thanks for getting back to me i just wanna backup my media files ie plex music movies pictures that's all i have on the server that's important to me.
So you recommend rsync,how would i go about mounting the drive on my windows pc to the server and setting it up so i could do a backup of the media with rsync thanks

---

### Post by mastablasta on 2014-06-12
ok so you have Raid1 but would liek to back it all up again on Windows disk :-O

rsync Will syncronise the disks. you can have a look at grsync which is a GUI frontend and if i am not mistaking it is available for Windows (deltacopy or something like that) as well. 
otherwise you would setup a chronjob that would do the syncing or backing up on your server. and then always at specified interval the sync would commence.

[http://rsync.samba.org/](http://rsync.samba.org/)

---

### Post by TheFu on 2014-06-12
> **mark103 said:**
> ok thanks for getting back to me i just wanna backup my media files ie plex music movies pictures that's all i have on the server that's important to me.
So you recommend rsync,how would i go about mounting the drive on my windows pc to the server and setting it up so i could do a backup of the media with rsync thanks

So 1 side of the 1 systems needs to access the other.  Going from Windows to Linux is probably easier - then have the Windows Machine pull the files.  robocopy is probably the best answer for that. Load up Samba on the Linux side ... use Nautilus to "share" the directories with the media files.  BTW - the media files are NOT everything when it comes to plex.  The metadata, downloaded subtitles, posters, actor information, .... it can be reproduced, but should be relatively tiny.  However, it needs to be backed up to non-NTFS storage.

If you want to go the other way - have Linux push to Windows ... have Windows share the storage and push the files from Linux, connect with a samba client (can also use almost any file manager program), just need to figure out how that storage can be accessed from a script, then use "rsync  -avz source target" . In 12.04, .gvfs is used to access Windows shares. Look under ~/.gvfs/ for the storage **after** you browse to it.  That changes in 14.04 ... mounts end up under /var or is that /media?  Anyway - gvfs rocks ... and sucks.  I prefer to use autofs to mount CIFS shares as needed.  That way it removes any manual point-n-click to connect after a reboot and the remote storage is consistently located where I want it.  On a single-user system, cifs mounts are fine.  Not so much for multi-user systems where CIFS requires extra effort to work as expected.

---

