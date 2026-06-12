---
title: "Dash Search of Mounted Partitions"
date: 2014-04-22
forum: General Help
---

### Post by ktz84 on 2014-04-22
I'm using a 128GB ssd therefore a lot of my files are stored on other disks and over a number of partitions of those disks although the majority are shows as links on the home folder. When I search the dash for files contained in these folders I don't see any relevant results even when filtering by files & folders to narrow results. Does the Dash not search mounted drives and if it is supposed is there what is the best to resolve this. Given the vast majority of my files are not in the home drive the dash is next to useless for me without the ability for it report the contents of these files and folders.

---

### Post by bkline on 2014-04-22
Make sure the other partitions are actually mounted. See [http://askubuntu.com/questions/137882/cant-ubuntu-dash-search-files-from-every-partition-of-my-hard-drive](http://askubuntu.com/questions/137882/cant-ubuntu-dash-search-files-from-every-partition-of-my-hard-drive)

---

### Post by ktz84 on 2014-04-22
Hi partitions are automouned on start up and they all show the up arrow in the file manager.

---

### Post by ktz84 on 2014-04-24
Can someone confirm that I should be able to search the files and folders on these mounted partitions? If I am anyone any other help they can offer?

---

### Post by ockelz on 2014-05-05
Same question here. I mounted a SMB share with fstab in my home folder,  zero / only used files from the mounted share as a result from a dash  search.  
I installed recoll and with the recoll gui i can perfectly  search my mounted SMB share. But a search in the dash doesn't bring up  the expected results (even when recoll is selected from the filtering).   I agree with the OP that mounted filesystems should be able to be  searched (by default?) with dash, otherwise the search function is  useless for me. 14.04 installed.

---

### Post by ktz84 on 2014-05-05
I tell you what I find the strangest thing of all. They devote all their resources to getting the dash to search online sources and give you results from Amazon, etc yet it can't find a file on it's own computer. Bizarre.

---

### Post by steeldriver on 2014-05-05
I think it depends *how and where* the filesystems are mounted - the dash search appears to be a GUI wrapper for the locate/mlocate command, which uses a database created and managed by updatedb. The /etc/updatedb.conf file tells updatedb to ignore certain mounted filesystems (mostly remote ones - nfs, cifs etc) but also certain mountpoint paths - including /media - and bindmounts

```

$ cat /etc/updatedb.conf
**PRUNE_BIND_MOUNTS="yes"**
# PRUNENAMES=".git .bzr .hg .svn[B]"
PRUNEPATHS="/tmp /var/spool /media /home/.ecryptfs"[/B]
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.glusterfs fuse.sshfs curlftpfs ecryptfs fusesmb devtmpfs"

```

I just tested this by doing a dash search for CONFIG.SYS (a file from the fuse-mounted Windows partition, on /media) - didn't find it at first, but did after I removed /media from the config file and ran sudo updatedb

[I don't recommend using /media for 'permanent' mount points - this was just a test]

---

### Post by ockelz on 2014-05-05
I couldn't agree less. I am trying unity (again..) and dash seems to  have a mind of its own. I'm old-fashioned and and i don't like fuzzy  semantic searches on my desktop, files and folders is the way to go for  me. And i still haven't figured out how to configure dash properly to do  this. If i cannot fully rely on the (suggested) results i will not use  it. In the early days i used google desktop search, and that engine  nailed every bit of information. I was hoping that dash would give me  the same experience. Recoll does a fine job though, so the only use of  dash for me for now is a huge application launcher.

---

### Post by ockelz on 2014-05-05
> **steeldriver said:**
> I think it depends *how and where* the filesystems are mounted - the dash search appears to be a GUI wrapper for the locate/mlocate command, which uses a database created and managed by updatedb. The /etc/updatedb.conf file tells updatedb to ignore certain mounted filesystems (mostly remote ones - nfs, cifs etc) but also certain mountpoint paths - including /media - and bindmounts

```

$ cat /etc/updatedb.conf
**PRUNE_BIND_MOUNTS="yes"**
# PRUNENAMES=".git .bzr .hg .svn[B]"
PRUNEPATHS="/tmp /var/spool /media /home/.ecryptfs"[/B]
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.glusterfs fuse.sshfs curlftpfs ecryptfs fusesmb devtmpfs"

```

I just tested this by doing a dash search for CONFIG.SYS (a file from the fuse-mounted Windows partition, on /media) - didn't find it at first, but did after I removed /media from the config file and ran sudo updatedb

[I don't recommend using /media for 'permanent' mount points - this was just a test]

TX steeldriver it worked!

I removed cifs and smbfs from the PRUNEFS="NFS...etc" line and did a sudo updatedb.
My network files are now showing up in dash.

---

### Post by steeldriver on 2014-05-05
OK... just be aware there *may* be other undesirable consequences (e.g. errors if/when then remote filesystems happen to be unmounted)

---

### Post by ktz84 on 2014-05-05
Brilliant. Thanks steeldriver. I removed /media in my instance ran the updatedb and my files now show. I note you said that permanent mounts aren't recommended for /media. How are they best handled as that's where I've mine mounted?

---

### Post by steeldriver on 2014-05-05
The usually recommended place is /mnt I think - the problem with /media is that's where the desktop session (gvfs) puts any 'user mounts' for removable media (CDROMs, pluggable USB devices etc.) and it can end up with stale and/or conflicting mount points - whereas /mnt should contain only things that you've specifically predefined (e.g. via /etc/fstab).

---

### Post by ktz84 on 2014-05-05
Ok thanks. Next time I install the OS I'll maybe change over however I'll leave it as it is for now as I have plex and other things looking at it's current location so it would be hassle to move now.

---

