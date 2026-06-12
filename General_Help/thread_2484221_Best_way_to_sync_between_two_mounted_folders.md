---
title: "Best way to sync between two mounted folders"
date: 2023-02-20
forum: General Help
---

### Post by uipojehdx on 2023-02-20
Hi there - I have ubuntu server installed on a miniPC on my home network with Roon installed (music server software). I have two folders mounted, one from my NAS and one an internal SSD. I am trying to sync between these two mounted folders, I will need to do this on a periodic basis.

I can SSH into Ubuntu Server (both server and ubuntu on 22.04.2 LTS) either via Ubuntu on an intel NUC or via another PC running Win 11. I have been trying to sync between the two mounted folders but I keep getting error messages when using freefilesync to do with permissions. 

What would be the easiest way to sync these folders on ubuntu server?

I am a novice user with linux.

Thanks.

---

### Post by MAFoElffen on 2023-02-20
Via ssh and rsync... ([https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories))

A lot of times, with media files synch'ed between folders I'll use unison called from cron, using a unison profile file and contains batch = true. ([https://ostechnix.com/how-to-synchronize-files-with-unison-on-linux/](https://ostechnix.com/how-to-synchronize-files-with-unison-on-linux/))

On other media files, where I share media file synchs between me and my son (during a visit), we'll use Midnight Commander, to see what is different between the two, and synch what we have together. ([https://www.reddit.com/r/linuxquestions/comments/4hoqfi/how_to_merge_directories_with_midnight_commander/](https://www.reddit.com/r/linuxquestions/comments/4hoqfi/how_to_merge_directories_with_midnight_commander/))

---

### Post by uipojehdx on 2023-02-20
Thank you for the reply, I will have a read!

---

### Post by uipojehdx on 2023-02-21
I see there is a bit of a learning curve! I am not sure I understand it yet. More reading it seems.

In the meantime, I was trying again in terms of freefilesync using SFTP this time, and these were the error messages I was getting

The recycle bin is not available for "sftp://xxxx@my IP here/mnt/NAS music mount/Music".
Operation not supported by device.
Ignore and delete permanently each time recycle bin is unavailable?
 
 
Cannot delete file "sftp://xxxx@MY IP here/mnt/SSD music/Music/music file.flac".
SSH_FX_PERMISSION_DENIED [libssh2_sftp_unlink]

This was happening even though I have the correct credentials. I can run a comparision between the two mounted folders but not make any changes.

Any thoughts anyone?

---

### Post by HermanAB on 2023-02-21
The best way? rsync

The access problems: 
Check that you have the same userid number on the two machines. The name may be the same, but the numbers may differ. To get around that, change it on one of the machines or use root.

---

### Post by uipojehdx on 2023-02-21
Thanks for the reply @hermanAB. 

> Check that you have the same userid number on the two machines. The name  may be the same, but the numbers may differ. To get around that, change  it on one of the machines or use root. 				

I am not sure I understand, I have the Ubuntu Sever,  Ubuntu, and a windows 11 machine. The Ubuntu Server has two mounted  folders, one from a NAS on my LAN and one from an internall SSD (these  are the two I am trying to sync). I can't use root with FreeFileSync as I  am running from a seperate machine, either ubuntu or windows via SSH. I  can't seem to run as root, but I can with another login which has  priveledges. I am probably missing something simple.

---

### Post by TheFu on 2023-02-21
For creating a delayed mirror of files and directories, rsync is the best tool regardless of platform, IMHO.

```
$ rsync -avz   {SOURCE} {TARGET}
```

Either can be local and the other can be remote or local.
If there's anything remote involved, then you'll need to wrap your head about the local userid and the remote userid for which files/directories can be read and written into.  On Unix-like OSes, this is controlled through simple permissions.
Most NAS devices support rsync directly, so they have that tool available to be used, so you don't need to use a mounted file system on the client which brings more overhead.  

While I don't do the same thing you do, for some media files, I do use rsync to periodically create backups.  The storage is all locally mounted, so the script as my userid and looks like this:
```
#!/bin/bash 

rsync="/usr/bin/rsync"
EXCLUDES="--exclude **/.Trash* --exclude lost+found --exclude ZCS-2012"
ionice $rsync -av --stats --progress $EXCLUDES --delete-during /d/D1/ /d/b-D1/
ionice $rsync -av --stats --progress $EXCLUDES --delete-during /d/D2/ /d/b-D2/
ionice $rsync -av --stats --progress $EXCLUDES --delete-during /d/D3/ /d/b-D3/
ionice $rsync -av --stats --progress $EXCLUDES --delete-during /d/D6/ /d/b-D6/
```

That script mirrors my primary media storage directories to backup storage directories, removing any files that don't exist in the "source" as it compares the list of files between the source and target.  The trailing '/' characters have special meaning in rsync (and most librsync tools). I find it is just easier to always use them to ensure any hidden files are sync'd too.

Hopefully, seeing a concrete example is helpful.  Using a script means the command is consistent.  I removed the -z option, since these are all local files. With a client/server rsync, leave the compression option in there.

If going across different systems, ensure that password-less ssh-keys are used, so the sync can happen overnight, automatically, via cron.
The **rsync** manpage is a masterpiece.  Well worth reading all the options, for example, I'm using the --delete-during option for a specific reason.  There are a few other delete control options.  If I didn't have any --delete-something option, new files would be copied over, but never removed.  I don't have that amount of storage to let my backup disks hold more and more and more and more files, though it would be nice.

As for permissions, if your userid can read the files and they are just media/data files, then it isn't really that important who owns them on the target storage, what group they are in or any of the other permissions/ACLs.  Of course, for real backups those things are 50% of what makes a good backup, especially for system files.

---

