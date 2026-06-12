---
title: "NFS script"
date: 2020-11-30
forum: General Help
---

### Post by wewantutopia on 2020-11-30
Hello,

I have this script that runs at startup that will mount NFS shares if I am connected to specific wifi networks.  This is a laptop so I'm not always around the NFS shares and don't want them mounted through fstab.  

```

#!/bin/bash


sleep 5s


killall clementine


umount /home/david/NFSMount/server_home; umount /home/david/NFSMount/Music; umount /home/david/NFSMount/Movies; umount /home/david/NFSMount/StorageDrive




wifi="'$(/sbin/iwconfig wlp3s0 | egrep ESSID | cut -d '"' -f 2)'"






if [ $wifi = "'wewantutopia1'" ]
    then
        sudo mount -t nfs 192.168.1.250:/media/"Storage Drive" /home/david/NFSMount/StorageDrive; sudo mount -t nfs 192.168.1.250:/home/david /home/david/NFSMount/server_home; sudo mount -t nfs 192.168.1.250:/media/"Storage Drive"/Movies /home/david/NFSMount/Movies; sudo mount -t nfs 192.168.1.250:/media/"Storage Drive"/Music /home/david/NFSMount/Music






elif [ $wifi = "'wewantutopia'" ]
    then
        sudo mount -t nfs 192.168.1.250:/media/"Storage Drive" /home/david/NFSMount/StorageDrive; sudo mount -t nfs 192.168.1.250:/home/david /home/david/NFSMount/server_home; sudo mount -t nfs 192.168.1.250:/media/"Storage Drive"/Movies /home/david/NFSMount/Movies; sudo mount -t nfs 192.168.1.250:/media/"Storage Drive"/Music /home/david/NFSMount/Music




elif [ $wifi = "'wewantutopia2'" ]
    then
        sudo mount -t nfs 192.168.1.250:/media/"Storage Drive" /home/david/NFSMount/StorageDrive; sudo mount -t nfs 192.168.1.250:/home/david /home/david/NFSMount/server_home; sudo mount -t nfs 192.168.1.250:/media/"Storage Drive"/Movies /home/david/NFSMount/Movies; sudo mount -t nfs 192.168.1.250:/media/"Storage Drive"/Music /home/david/NFSMount/Music




fi


sleep 2s


clementine

``` 

I had this setup previously with GVFS (which is WAY too slow) and worked fine; but, since mount requires root privileges it's, of course, not working.  (I have a sudoers.d file for umount but won't do that for mount for obvious reasons)

How can I make mount work with this script?

Thanks!!

---

### Post by TheFu on 2020-11-30
I wouldn't re-invent the wheel. Use **autofs** for USB and sometimes available NFS mounts.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Autofs will mount storage when requested. Just try to access the storage using any program, including ls/bash/whatever, and autofs will attempt to mount it. Performance is identical to the fstab entries and we have the same control over mount options to get the best performance.

Autofs will un-mount unused storage automatically a few minutes after it isn't used any longer. That's very handy. 

BTW, mounting NFS under any HOME directory is an anti-pattern.  Best to mount that stuff under /nfs or /mnt/nfs/ or /media/net/ and use symbolic links from your HOME out to each place, if you like.

First thing I'd do with your script is make it readable - i.e. fit so I don't have to scroll to the right to see stuff.  Newlines are free.

---

### Post by wewantutopia on 2020-11-30
Thanks for the reply and help!

I just finished researching and setting up autofs for my NFS shares and it worked.  Thanks!  I have changed the mount point to /mnt, thanks.

I added these lines to auto.master

```
/-  /etc/auto.1home  -nosuid,  noowners
/-  /etc/auto.2storagedrive  -nosuid,  noowners
/-  /etc/auto.3music  -nosuid, noowners
/-  /etc/auto.4movies  -nosuid, noowners
```

Then added this text to each of the files (with correct paths of course

```
/mnt/"Server Home" -fstyle=nfs,user,nolock,nosuid,rw 192.168.1.250:/home/david
```

No problem accessing the shares, though they are a BIT slower than a direct "mount".

The new autofs mounts, however, aren't showing up on my desktop or dock (Ubuntu 20.04) or the Nautilus side panel.  Any ideas how to make that work?

Thanks!

---

### Post by TheFu on 2020-12-01
The mount isn't slower once it is made, but if the drive is spun down, it will need to spin up to be mounted and that can take 2-10 seconds.
Mounts appear as local storage, so if you want to bookmark a location, then you can.  You might want to check out the "--ghost" option if you use a GUI.  I don't use nautilus and barely use any GUI file manager. My shell and file globbing skills are much faster.

Or you could use symbolic links from somewhere inside your HOME to those autofs mount locations.

My auto.master:
```
/-      /etc/auto.nfs --timeout=60 --ghost
```

Example lines from my auto.nfs file:
```
$ more /etc/auto.nfs 

/d/D1 -fstype=nfs,proto=tcp,intr,rw,async  istar:/d/D1
/d/D2 -fstype=nfs,proto=tcp,intr,rw,async  istar:/d/D2
/d/D3 -fstype=nfs,proto=tcp,intr,rw,async  istar:/d/D3
```

BTW, your post above appears to have typos in both the master and actual mount lines. It is normal to put all NFS mounts into 1 file, so the auto.master only needs 1 line.  But you can do whatever you like if complexity is ok.
I have 1 line/file for NFS mounts, another for USB devices and another for CIFS mounts. There really isn't any reason not to merge those into 1 file, just habit to keep the different mount types separate, I suppose.

It is good that you found the **/-** method.  That is not intuitively obvious, but it does make for less confusion than the other method to specify relative mount points.

I can't find any mention of -nosuid,  noowners options for the auto.master in the manpage. I'm surprised that didn't blow up.

If you are trying to share HOME directories across multiple systems that are used via an LDAP authentication, there are special autofs and LDAP settings that are better.  If that is not the intent, files shared across systems probably shouldn't be located inside HOME on any system.

We control the suid ability in the local storage mounts (fstab) and export files on the NFS server.  Clients really don't have control over security.

---

### Post by wewantutopia on 2020-12-01
Thanks again for the replies!

I was messing around with symlinks but I don't think I like that option.  Since they're just "folders" they can be deleted (accidentally) trashing all the remote data with them.  That's one reason I was preferring "monut"; they appear a drives.  

My samba shares using GVFS appear a network folders that can be unmounted as a drive. 

I'm using "server home" just for moving quick files from one device to the other (not sharing home directories)

I'm curious, what are the typos in the master and mount lines?

---

### Post by TheFu on 2020-12-01
> **wewantutopia said:**
> I was messing around with symlinks but I don't think I like that option.  Since they're just "folders" they can be deleted (accidentally) trashing all the remote data with them.  That's one reason I was preferring "monut"; they appear a drives.  

Deleting a symlink would just delete the link, not where it points. You still would need to mount the storage.  Perhaps you are confusing a bookmark with a symlink?  Symbolic links or soft-links are part of the file system, not some GUI addon.

> **wewantutopia said:**
> My samba shares using GVFS appear a network folders that can be unmounted as a drive. 
GVFS is dog slow compared to a real CIFS mount.  Do a little testing, you'll see.  "Real" mounts show up in the mtab and are shown when we type 'mount' without any options in a shell.

> **wewantutopia said:**
> I'm using "server home" just for moving quick files from one device to the other (not sharing home directories)  For that, I'd probably just use a bi-directional rsync, though I generally use a "system of record" idea and all other locations are considered read-only, copies, temporary.

> **wewantutopia said:**
> I'm curious, what are the typos in the master and mount lines?

_fstyle_ isn't a valid entry.
_-nosuid,  noowners_ are not valid.

---

