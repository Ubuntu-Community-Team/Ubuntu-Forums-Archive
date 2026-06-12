---
title: "Samba? Xubuntu Client"
date: 2007-01-06
forum: General Help
---

### Post by Frankly3D on 2007-01-06
Hi 

Trying to link a Xubuntu Client with an FC6 Samba server.
Had a look at [http://ubuntuforums.org/showthread.php?t=248656](http://ubuntuforums.org/showthread.php?t=248656)

but some problems.

----------------------------------------------------------------------------------
me@xubuntu:~$ smbclient -L fc6
Password:
Domain=[FC6] OS=[Unix] Server=[Samba 3.0.23c-2]

        Sharename       Type      Comment
        ---------       ----      -------
        store00         Disk      File Directories
        store01         Disk      File Directories
--------------------------------------------------------------------------------------
list the shares, ok.

fstab has been edited:
-------------------------------------------------------------------------------------------------------
//FC6/store00   /mnt/store00  cifs  username=xubuntu,password=password  0   0
//FC6/store01   /mnt/store01  cifs  username=xubuntu,password=password  0   0
--------------------------------------------------------------------------------------------------------

I ran sudo mkdir for /mnt/store00 (01)


but mount -a brings:
------------------------------------------------------------------------------------------------------------
sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on //FC6/store00,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //FC6/store01,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
-----------------------------------------------------------------------------------------------------


dmesg | tail brings:
--------------------------------------------------------------------------------------------------
dmesg | tail
[17179710.572000]  CIFS VFS: cifs_mount failed w/return code = -22
[17179710.572000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180037.504000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180081.440000] smb_fill_super: missing data argument
[17180117.828000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180117.828000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180748.204000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180748.204000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180887.828000]  CIFS VFS: cifs_mount failed w/return code = -22
[17180887.828000]  CIFS VFS: cifs_mount failed w/return code = -22

-----------------------------------------------------------------------------------------------------

At a loss

Frank

---

### Post by metoor30 on 2007-12-19
I had this same problem when switching a Slackware system from smbfs to cifs.  Nothing else changed.  I was able to get around this error by changing //<hostname>/<share> to //<IP Address>/<share>.  I'm not sure why this work, the hostname was in the hosts file.

If you still have problems, make sure the spelling of all the options listed in the fstab are correct.

---

### Post by metoor30 on 2007-12-19
Didn't realize that this post was so old, but hope it helps someone.

:)

---

### Post by tierra on 2007-12-20
> **metoor30 said:**
> Didn't realize that this post was so old, but hope it helps someone.

That was pretty good timing actually. You can be happy it's helped at least one person now. :)

Thanks

---

### Post by bernied on 2008-02-02
> **metoor30 said:**
> I had this same problem when switching a Slackware system from smbfs to cifs.  Nothing else changed.  I was able to get around this error by changing //<hostname>/<share> to //<IP Address>/<share>.  I'm not sure why this work, the hostname was in the hosts file.
This worked for me too. Thanks metoor.

Curiously, it looks like the problem will be resolved in time, as it applies to my Kubuntu Fiesty install, but not to a Debian testing install, where I am able to use host names (not IP addresses) with no problems. 
On Fiesty:
```
$ smbclient --version
Version 3.0.24
```
On Debian testing:
```
$ smbclient --version
Version 3.0.28
```

Maybe it is fixed in gutsy??

---

### Post by dturanski on 2008-02-05
I got the same thing in gutsy. IP address works.
>> smbclient --version
Version 3.0.26a

---

### Post by sean4u on 2008-02-08
Hello Thread. I solved this exact same problem on a new Xubuntu install by installing the smbfs pacakge. The error appeared for me because mount.cifs was missing. And I spotted a hint about that on an archlinux thread!

Hope this helps.
Sean

---

### Post by r m h on 2008-04-06
Ubuntu 7.10 doesn't appear to install smbfs by default.

The answer for me was the same as for sean4u - install smbfs
...and as you can see, I was able to use the server name not its IP address

hope this summary helps someone, someday:

root@glacier:~# mount -t cifs -o username=user //server/music2 /mnt/music2 ; echo "" ; dmesg | tail -1
mount: wrong fs type, bad option, bad superblock on //server/music2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

[58268.423629]  CIFS VFS: cifs_mount failed w/return code = -22

# now try accessing 'server' by its' IP address

root@glacier:~# mount -t cifs -o username=user //192.168.11.56/music2 /mnt/music2 ; echo "" ; dmesg | tail -2
mount: block device //192.168.11.56/music2 is write-protected, mounting read-only
mount: cannot mount block device //192.168.11.56/music2 read-only

[59990.266151]  CIFS VFS: Send error in SessSetup = -13
[59990.395423]  CIFS VFS: cifs_mount failed w/return code = -13

# now try passing the read-write flag and the workgroup

root@glacier:~# mount -t cifs -o rw,username=user,workgroup=ICE //192.168.11.56/music2 /mnt/music2 ; echo "" ; dmesg | tail -2
mount: block device //192.168.11.56/music2 is write-protected, mounting read-only
mount: cannot mount block device //192.168.11.56/music2 read-only

[67901.827099]  CIFS VFS: Send error in SessSetup = -13
[67901.957115]  CIFS VFS: cifs_mount failed w/return code = -13

# install smbfs and try again, using server name, not IP

root@glacier:~# apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  smbfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 485kB of archives.
After unpacking 1126kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main smbfs 3.0.26a-1ubuntu2.3 [485kB]
Fetched 485kB in 1s (275kB/s) 
Selecting previously deselected package smbfs.
(Reading database ... 104893 files and directories currently installed.)
Unpacking smbfs (from .../smbfs_3.0.26a-1ubuntu2.3_i386.deb) ...
Setting up smbfs (3.0.26a-1ubuntu2.3) ...

root@glacier:~# mount -t cifs -o rw,username=user,workgroup=ICE //server/music2 /mnt/music2
Password: <enter password for user 'user' on server 'server'>

root@glacier:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            147850940  27082740 113257816  20% /
varrun                 1037972        92   1037880   1% /var/run
varlock                1037972         0   1037972   0% /var/lock
udev                   1037972        80   1037892   1% /dev
devshm                 1037972         0   1037972   0% /dev/shm
lrm                    1037972     34696   1003276   4% /lib/modules/2.6.22-14-generic/volatile
//server/music2    3417763836 3200977576 216786260  94% /mnt/music2

---

### Post by dannyboy1121 on 2008-06-26
smbfs ... ahhhhhHHHhhhh

Thanks for posting this .. I was bashing my head against a brick wall on this one trying to sort out an autofs issue on ubuntu-eee for my little eeepc

---

