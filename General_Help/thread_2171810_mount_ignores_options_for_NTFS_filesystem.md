---
title: "mount ignores options for NTFS filesystem"
date: 2013-09-01
forum: General Help
---

### Post by arielCo on 2013-09-01
I'm trying to have my NTFS partitions mount with execute permissions, to no avail.

From 'man ntfs-3g':
> 
   Access Handling and Security
       By  default,  files  and  directories  are  owned by the effective user and group of the mounting process, and
       everybody has full read, write, execution and directory browsing permissions.  You can also assign permissions
       to a single user by using the uid and/or the gid options together with the umask, or fmask and dmask options.

       Doing so, Windows users have full access to the files created by ntfs-3g.


> 
       umask=value
              Set the  bitmask of the file and directory permissions that are not present.  The  value  is  given  in
              octal. The default value is 0 which means full access to everybody.

       fmask=value
              Set  the   bitmask  of  the  file  permissions  that are not present.  The value is given in octal. The
              default value is 0 which means full access to everybody.

       dmask=value
              Set the  bitmask of the directory permissions that are not present. The value is given  in  octal.  The
              default value is 0 which means full access to everybody.


After setting *mask,exec in /etc/fstab, I started trying manually.

Preliminaries:
```

$ sudo parted  /dev/sdb1 print
Model: Unknown (unknown)
Disk /dev/sdb1: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ntfs

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e93dba9f-a99d-40ec-a0bc-868f81f9b69e /               ext4    noatime,discard,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=c5742f81-7520-4c2e-9e44-e2e0872d1c69 none            swap   sw,noauto               0       0
tmpfs /tmp tmpfs nodev,nosuid,size=6G 0 0
# UUID="46A8DB5D20C177B0" /media/wd_red_2tb ntfs-3g rw,fmask=022 0 0

$ id
uid=1000(ariel) gid=1000(ariel) groups=1000(ariel),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),107(lpadmin),124(sambashare),126(wireshark),128(debian-tor)

$ groups $USER
ariel : ariel adm cdrom sudo dip plugdev **fuse** lpadmin sambashare wireshark debian-tor

```

So, let's try it:
```

$ sudo mount -t ntfs-3g -o uid=1000,exec,fmask=0000,umask=0000,dmask=0000 /dev/sdb1 /media/wd_red_2tb/

$ ls -l /media/wd_red_2tb/COMSOL43/bin/comsol
-rw------- 1 ariel ariel 28754 Jun 29 19:27 /media/wd_red_2tb/COMSOL43/bin/comsol

```

The *mask and exec switches are either not being passed, or ignored.

But, are the options being passed at all?
```

$ sudo umount /dev/sdb1
$ sudo mount -t ntfs-3g -o uid=0,exec,fmask=0000,umask=0000,dmask=0000 /dev/sdb1 /media/wd_red_2tb/
$ ls -l /media/wd_red_2tb/COMSOL43/bin/comsol
-rw------- 1 ariel ariel 28754 Jun 29 19:27 /media/wd_red_2tb/COMSOL43/bin/comsol

$ sudo umount /dev/sdb1
$ sudo mount -t ntfs-3g -o uid=113,exec,fmask=0000,umask=0000,dmask=0000 /dev/sdb1 /media/wd_red_2tb/
$ ls -l /media/wd_red_2tb/COMSOL43/bin/comsol
-rw------- 1 ariel ariel 28754 Jun 29 19:27 /media/wd_red_2tb/COMSOL43/bin/comsol

```

Of course I've already searched the better part of an hour for solutions, and what seems to work for everyone doesn't for me.
Any ideas?

---

### Post by TheFu on 2013-09-01
I think doing this is a big security risk - but whatever, it is your box.
I was under the impression that the ntfs-3g drivers were not used anymore.  I've been using the "cifs" drivers for years.

Something like:
```
sudo mount -t cifs //win7-crap/K $MNT_PNT  -o iocharset=utf8,nounix,uid=thefu
```

**man mount** explains lots of stuff about this. **man mount.cifs** gets into more specifics for this specific driver. Be certain to include the utf8 character set in the options.

Anyway, I hope this helps. There are many old pages on the internet with 5 yr old data.

---

### Post by arielCo on 2013-09-01
The 0000 masks were only to test that ntfs-3g was getting the options (note that I also try passing other UIDs), all in vain since it still mounts as 0600. What's weirdest is that it also "guesses" my UID - it MUST be getting it from somewhere.

I'll have a read about CIFS - thanks for the idea.

**Edit: **CIFS rang a bell for a reason: [it's the modern version of SMB]("http://en.wikipedia.org/wiki/CIFS"), which as far as I know is only useful for *network resources*. This is a local disk I'm trying to mount, so I don't know how it'd help me. It's still good to know that I can mount SMB shares instead of transfering through smbclient.

---

### Post by arielCo on 2013-09-01
Funny, I ejected the drive in Nautilus (had to authenticate), and from then on everything works, masks and uid, gid:

```
$ sudo mount -t ntfs-3g -o uid=113,gid=113,fmask=077,dmask=077 /dev/sdb1 /media/wd_red_2tb
$ sudo ls -l /media/wd_red_2tb/COMSOL43/bin/
total 81
-**rwx------** 1 **pulse utempter**   433 Apr 27  2012 browser
-**rwx------** 1 **pulse utempter** 28754 Jun 29 19:27 comsol
-**rwx------** 1 **pulse utempter** 28754 Apr 27  2012 comsol.bk
-**rwx------** 1 **pulse utempter**  2020 Apr 27  2012 comsolpath.txt
d**rwx------** 1 **pulse utempter**  4096 Apr 30  2012 glnx86
d**rwx------** 1 **pulse utempter**  4096 Sep  1 22:12 glnxa64
d**rwx------** 1 **pulse utempter**     0 Apr 27  2012 jar
-**rwx------** 1 **pulse utempter**  2363 Apr 27  2012 setuplibpath
```

Riddle me that! :-k

---

### Post by TheFu on 2013-09-02
Nautilus causes more issues than it solves around mounting, IMHO. I'm probably a minority.

---

### Post by arielCo on 2013-09-02
> **TheFu said:**
> Nautilus causes more issues than it solves around mounting, IMHO. I'm probably a minority.

So you too think that it was Nautilus? It makes a bit of sense, since I used to mount it manually under [FONT=monospace]/media/$USER/<label>[/FONT]; I think it involves [FONT=monospace][FONT=lucida console]udisks[/FONT][/FONT]. As seen in the original post, something was overriding the permissions and uid:gid to rw------ and $USER:$USER even though [FONT=monospace]mount[/FONT] is always run as root, possibly by remounting the volume.

---

### Post by TheFu on 2013-09-02
I think that the way nautilus mounts things is half-assed. It doesn't make the mount available system-wide.
I also think that having multiple mounts of the same storage can be confusing.  The eject released the stale mount.  **umount** is the command to do that for CLI.  Mounting the same storage multiple times is bad. I think a mount-count is maintained, so unmounting multiple times might be necessary.

---

### Post by arielCo on 2013-09-02
I didn't see it mounted multiple times in my case. Maybe the reason it doesn't mount system-wide is that Nautilus is intended for personal use, and it's a volume that *you* asked to be mounted and don't want to share with other users. Maybe a "Share with other users" option would help. In any case interfering with the mount command is unwelcome shenanigans.

---

### Post by Morbius1 on 2013-09-03
It's actually been a long progression to get to this point.

The "Nautilus" method is for mounting things automatically that are not in fstab and adopts the mechanism used to mount external usb storage devices. Back in the olden tymes when you plugged in an ntfs usb stick it would mount to /media/LABEL with permissions of 777 making it available to anyone. Then all of a sudden it was changed to set ownership = the user that inserted it and permissions of 700 making it available only to that user.

The odd man out of this process was something formatted in a Linux fileystem like ext4. It would mount to /media/LABEL but you could set it to have whatever permissions you wanted. What to do - what to do ......

The answer was to create a new mount point parent: /media/$USER. And instead of having a simple permissions schema it was set by the system using Access Control LIst to limit access to everything beyond it to only the logged in user. Now all these non-system disks will have the same access restrictions just like NTFS does.

It all makes perfect sense if the decision to do this was in the hands of someone who doesn't use Linux himself.

---

### Post by TheFu on 2013-09-03
@Morbius1 - I'm still on 10.04 and 12.04 systems and haven't seen those new mount points. Actually, I disable the automatic mounting of media - it is a security issue to me.  Obviously, I disagree with automounting anything that wasn't setup by root to be mounted.

I'm a fringe user, clearly.  Other people have different desires, but in the meantime, I'll be manually mounting storage and **Knowing** exactly what permissions are provided to that storage on the system.

I just hope the automount stuff disables setuid/setgid and adds a noexec to the mount options too.

---

