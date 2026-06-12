---
title: "Trouble downloading torrents!"
date: 2007-08-21
forum: General Help
---

### Post by Pillzbury on 2007-08-21
Okay, I'm assuming this is less of a torrent issue than a general system issue.  

First off, I've been downloading torrents without problems for several weeks now, however last night whenever trying to open a torrent in kTorrent, I get an error message:

"Cannot
create /media/hdb1/Downloading/xxxxxxxxxxxxxxxx/xxxx/xxxxxxx.xxx
No such file or directory"

(xxxx's of course being the directory and path to the first file in the torrent)

This happens after the initial add box where you can select which files to download and mark the torrent as user controlled.

I tried uninstalling and reinstalling kTorrent and it still does the same thing.

Next I tried to open the torrent in uTorrent through wine.  The torrent will load perfectly fine, however when I start it, it will download about 1mb before the Status column changes from "Downloading" to "Error: No access to memory location"

Because hdb1 is an NTFS partition, I thought maybe it was a problem with ntfs-3g, so I did:

"sudo apt-get autoremove ntfs-3g"

followed by:

"sudo apt-get install ntfs-3g"

I am still getting the same error on both programs.  Can anyone help?

EDIT:  I tried uninstalling ntfs-3g again, then rebooting, reinstalling, and rebooting once more.  Still no luck

---

### Post by astralsin on 2007-08-21
are you sure hdb1 is mounted? issue the mount command at the command line and look for a /dev/hdb1 line

---

### Post by Pillzbury on 2007-08-21
Here is the output from my mount command:

```
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdb1 on /media/hdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

### Post by g2g591 on 2007-08-21
also be sure to use ntfs-config to allow writing! by default ntfs-3g isn't used, thats why you must use ntfs-config to make it work (all you must do is check one or two boxes and hit ok)

---

### Post by Pillzbury on 2007-08-22
Both boxes are check in ntfs-config.

Are there any good programs for examining an ntfs hard drive in linux?  I have spinrite by grc, however that requires me to run it at boot and it takes a loooooooong time to examine a 250gb hd


Edit:  A new issue has arised.  Whenever I try to extract files on hdb1 i get error: 

"Cannot create /media/hdb1/Downloaded/Torrents/Downloading/xxxxxxxxxx.xxx
Input/output error"

and when trying to create a new folder, I get error: 

"Error creating new folder.

Error "I/O error" creating new folder."

Dunno if its worth mentioning, but hda1 is also an NTSC drive and I can create folders on it without issue.

---

