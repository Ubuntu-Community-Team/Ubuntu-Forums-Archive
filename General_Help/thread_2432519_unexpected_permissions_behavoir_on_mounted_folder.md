---
title: "unexpected permissions behavoir on mounted folder"
date: 2019-12-03
forum: General Help
---

### Post by cbc02009 on 2019-12-03
Hello,

I am running Ubuntu desktop inside of an unraid VM. I am passing a folder to the VM using 9p. The folder is a mounted zfs filesystem. Even though the folder has 777 permissions, I don't seem to be able to create subfolders in it without using sudo.

Here's the ls -al followed by the command and the output:

```

*****@SakuraBittorrent:~$ cd /unraid
*****@SakuraBittorrent:/unraid$ ls -al
total 9
drwxrwxr-x  4 ***** ***** 4096 Dec  3 05:41 .
drwxr-xr-x 21 root  root  4096 Nov 30 19:07 ..
drwxrwxrwx  2    99 users    2 Dec  3 18:40 Bittorrent
drwxr-xr-x  2 root  root     0 Dec  3 18:16 torrents
*****@SakuraBittorrent:/unraid$ mkdir Bittorrent/test
mkdir: cannot create directory &#8216;Bittorrent/test&#8217;: Operation not permitted

```



I've also verified that the user is a member of the 'users' group.

here's the relevant entry in /etc/fstab:
```
Bittorrent /unraid/Bittorrent 9p noauto,x-systemd.automount,x-systemd.device-timeout=10,timeo=14,x-systemd.idle-timeout=0,trans=virtio,rw 0 0
```

I would be happy to provide any additional information that might be needed. I know this is most likely an unraid problem, but I figured I'd post here on the off chance it isn't. Thanks!

---

### Post by TheFu on 2019-12-04
Just a guess, but the "99" being shown means that the local system doesn't have a userid with that number, so any uid lookup is failing.
Also, if the 
```
drwxrwxr-x  4 ***** ***** 4096 Dec  3 05:41 .
```
is exactly what you are seeing, then the username and groupname are bogus. Directory permissions control whether files can be added or removed inside that directory.   . (dot) is the current directory.

Why not just make the Bittorrent directory owned by the userid running the BT program?

---

### Post by Impavidus on 2019-12-05
> **cbc02009 said:**
> 
```

*****@SakuraBittorrent:/unraid$ mkdir Bittorrent/test
mkdir: cannot create directory ‘Bittorrent/test’: **Operation not permitted**

```


I'm puzzled. Note that the error message is "Operation not permitted" (EPERM), not "Permission denied" (EACCES) or "Read-only file system" (EROFS). This suggests that```
EPERM  The filesystem containing pathname does not support the creation of directories.
```which makes me wonder why root can create new directories. Or can't root? I'm not familiar with this filesystem type.

---

### Post by TheFu on 2019-12-05
Note, the OP is using a plan9 file system.  We don't see those here very much.  All sorts of funky rules exist for that use.
[https://www.kernel.org/doc/Documentation/filesystems/9p.txt](https://www.kernel.org/doc/Documentation/filesystems/9p.txt)

Just because the client-side says the mount is rw, that doesn't mean the server-side is sharing it read-write.

With NFS, local root gets converted to the nobody userid as far as the NFS file system is concerned.  Does plan9 behave that way too?

---

### Post by cbc02009 on 2019-12-07
I'm very sorry for the delay in responding to this thread, It's been a  pretty hectic week. I've managed to narrow the problem down to something  ZFS related. If I have two shares mounted using the identical  /etc/fstab entry posted above, but one is ZFS and the other is just a  normal unraid share, the normal unraid share works as expected, but the  ZFS share does not.

> **TheFu said:**
> Just a guess, but the "99" being shown means that the local system doesn't have a userid with that number, so any uid lookup is failing.
Also, if the 
```
drwxrwxr-x  4 ***** ***** 4096 Dec  3 05:41 .
```
is exactly what you are seeing, then the username and groupname are bogus. Directory permissions control whether files can be added or removed inside that directory.   . (dot) is the current directory.

Why not just make the Bittorrent directory owned by the userid running the BT program?

Sorry, that's just me being paranoid and removing my username from the post. Unraid wants its shares to be chown nobody:users (99:100), from what I've read, and doesn't really like that being changed. 

> **Impavidus said:**
> I'm puzzled. Note that the error message is "Operation not permitted" (EPERM), not "Permission denied" (EACCES) or "Read-only file system" (EROFS). This suggests that```
EPERM  The filesystem containing pathname does not support the creation of directories.
```which makes me wonder why root can create new directories. Or can't root? I'm not familiar with this filesystem type.

With this particular share, I can do anything I want in the folder from within the VM as long as it's with sudo. 

> **TheFu said:**
> Note, the OP is using a plan9 file system.  We don't see those here very much.  All sorts of funky rules exist for that use.
[https://www.kernel.org/doc/Documentation/filesystems/9p.txt](https://www.kernel.org/doc/Documentation/filesystems/9p.txt)

Just because the client-side says the mount is rw, that doesn't mean the server-side is sharing it read-write.

With NFS, local root gets converted to the nobody userid as far as the NFS file system is concerned.  Does plan9 behave that way too?

I can't pretend to know anything about plan9. The only reason I used it is that it came up first when I googled how to mount unraid zfs shares inside linux VMs.

---

### Post by TheFu on 2019-12-07
NFS servers work fine directly sharing from ZFS file systems.  Going through p9 is adding an extra unneeded layer.

ZFS supports NFS shares via the *set sharenfs=* construct.  No need for /etc/exports config. 
On the client side, the mount command is the normal NFS mount, as expected.
[https://docs.oracle.com/cd/E23824_01/html/821-1448/gayne.html#scrolltoc](https://docs.oracle.com/cd/E23824_01/html/821-1448/gayne.html#scrolltoc)
I haven't tried these on Linux.

---

### Post by cbc02009 on 2019-12-07
> **TheFu said:**
> NFS servers work find directly sharing from ZFS file systems.  Going through p9 is adding an extra unneeded layer.

ZFS supports NFS shares via the *set sharenfs=* construct.  No need for /etc/exports config. 
On the client side, the mount command is the normal NFS mount, as expected.
[https://docs.oracle.com/cd/E23824_01/html/821-1448/gayne.html#scrolltoc](https://docs.oracle.com/cd/E23824_01/html/821-1448/gayne.html#scrolltoc)
I haven't tried these on Linux.

Thanks for the info! I'll give it a shot this afternoon.

---

### Post by cbc02009 on 2019-12-07
Thanks! with your guide I was able to get NFS shares on my ZFS filesystem!

---

