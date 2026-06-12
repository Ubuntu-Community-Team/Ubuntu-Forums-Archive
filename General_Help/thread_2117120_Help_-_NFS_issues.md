---
title: "Help - NFS issues"
date: 2013-02-17
forum: General Help
---

### Post by cscj01 on 2013-02-17
I have two PC's, both of which are currently using Ubuntu 12.04; one is x64 and the other x32. I'll refer to them respectively as CP1 and CP2.

CP1 is what I use for my work. I have Ubuntu on one internal hard drive (I'll call it my system drive), and all of my data on a separate internal hard drive (I'll call it my data drive). I have one external USB drive I use to occasionally clone my system drive using Clonezilla. I have a dual boot set up on the system drive with XP SP3, but I recently installed Virtualbox and created an XP VM. I plan to get rid of the separate XP partition when I get all the XP software I need working in the VM.

CP2 is my wife's computer, and her use is a bit more casual than mine. I have two internal hard drives, one being the system drive and one being the data drive in the sense of CP1. I have two USB external hard drives attached to CP2. One is used to clone the CP2 system drive, and the other is used to backup the data drive of CP1. I run luckyBackup on CP1 to accomplish the backup of the data drive on CP1 to the external USB hard drive on CP2. I also have a dual boot on CP2, and have recently moved my wife to Ubuntu.

Before, when CP2 was only XP, I used Samba to share the USB external hard drive on CP2 with CP1. That allowed me to mount the USB drive on CP1 in order to run luckyBackup. After installing Ubuntu on CP2, I decided to create an NFS Home Network rather than Samba. That setup has CP2 as the server and CP1 as the client. I have included my current files and a couple of command results for the two systems below.

While struggling with the problems that began after I had to reboot the server (CP2), some odd things (at least to me) have come to light. The first concerns directory ownership and permissions. ON CP2, I created two directories to export my backup USB drive so I could have it mounted as an NFS share on CP1 to execute luckyBackup. I called these /export and /export/cp1data. The owner was root and they both had 777 permissions. However, when I reboot CP2, /export/cp1data has my wife as owner, and only she has access. Group and Others have no access. The mounted share has an owner of nobody and a group of nogroup on CP1 with only nobody having any access at all, and I have access problems on CP1 when I try to access the mounted CP2 share on CP1. I included a mount in /etc/fstab as seen below.

The second problem seems to occur randomly. If I mount the CP2 share on CP1, it will sometimes disappear. By this I mean if I browse to the location on CP1 which is /mnt/cp1data, I show no files. However, those files were there after I mounted cp2.local as indicated below. And if I come back some time later, they may show again when I browse to /mnt/cp1data.

A third problem presents itself this way. If I mount the CP2 share on CP1, on some occasions when I browse to /mnt/cp1data, Nautilus goes into a busy state and will not end. If I use Systems Monitor to check it, Nautilus shows as Uninterruptible. I have found no way to kill the process, either from Systems Monitor or from a terminal as super user. I am forced to restart CP1.

Finally, a fourth issue is trying to unmount the mounted share. If I use sudo umount, I am told the resource is busy. If I try umount.nfs, I am told the mounted system is not an NFS file system.

So I have so many issues happening, I cannot sort things out. Is mounting a share that is on an external USB drive a problem within itself? Why can I not unmount the share? Why does the share disappear at times. Why does Nautilus go into a state that does not allow me to kill the process? Why am I told the share is not an NFS system when it was mounted as one?

Hopefully, someone can sort out some of these issues because I am just trying my first NFS configuration. Any suggestions/answers will be most appreciated.

Here's my configuration info.

From the NFS Server:

/etc/fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=a00cc678-008c-496a-9fc6-213250ba5b6b / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=a471427e-e168-46b3-8108-c183c3c4fd38 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# CP1 Data Drive Backup share
/media/Ubuntu_Data_Backup/Data /export/cp1data none bind 0 0
/etc/exports
> 
# /etc/exports: the access control list for filesystems which may be exported
# to NFS clients. See exports(5).
#
# Examples for NFSv2 and NFSv3:
# /srv/homes hostname1(rw,sync,fsid=0,crossmnt,no_subtree_check )
#
# Example for NFSv4:
# /srv/nffs4 gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nts4/homes gss/krb5i(rw,sync,no_subtree_check)
# Exports for CP1 Data Backups
/export 192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/cp1data 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/etc/idmapd.conf
> 
[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
/etc/default/nfs-common
> 
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
# Should rpc.statd listen on a specific port? This is especially useful
# when you have a port-based firewall. To use a fixed port, set this
# this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
# For more information, see rpc.statd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_IDMAPD=yes
NEED_GSSD=no # no is the default
/etc/default/nfs-kernel-server
> 
# Number of servers to start up
# To disable nfsv4 on the server, specify '--no-nfs-version 4' here
RPCNFSDCOUNT=0

# Options for rpc.mountd
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS=--managegids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=no # no is the default

# Options for rpc.svcgssd.
RPCSVGSSDOPTS=

# Options for rpc.nfsd.
RPCNFSDOPTS=
```

showmount -e cp2
Export list for cp2:
/export/cp1data       192.168.1.0/24
/export               192.168.1.0/24
```


From the NFS Client:

/etc/fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#Entry for /dev/sdb1 :
UUID=00AE2EA54F4183A2 /media/Data ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
#Entry for /dev/sda1 :
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
#Entry for Samba Share drive g on cp2
#//cp2/g /mnt/cp2 smbfs iocharset=utf8,uid=1000 0 0

#Entry for NFS Server on drive g on cp2
cp2.local:/ /mnt nfs4 _netdev,auto 0 0
/etc/idmapd.conf
> 
[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
/etc/default/nfs-common
> 
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
# Should rpc.statd listen on a specific port? This is especially useful
# when you have a port-based firewall. To use a fixed port, set this
# this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
# For more information, see rpc.statd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_IDMAPD=yes
NEED_GSSD=no # no is the default
```


df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc2       421G  176G  224G  44% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  1.1M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  204K  2.9G   1% /run/shm
/dev/sdb1       1.4T  873G  525G  63% /media/Data
/dev/sda1        31G   23G  8.0G  75% /media/sda1
cp2.local:       47G  4.1G   41G  10% /mnt
/dev/sdc1        31G   20G   12G  64% /media/C48C88E98C88D6F8_
/dev/sdc2       421G   89G  311G  23% /media/b61632e9-7186-4ec9-9e4c-214c01d39a4e
```

---

### Post by LewisTM on 2013-02-17
First of all, exporting a USB drive is no problem at all as long as it is formatted with a Linux filesystem. You should know that the owner of the drive becomes the owner of the export, regardless of the ownership of the dir you use as bind mount.

The first problem sounds like an ID mismatch problem, where the USB drive's owner UID (your wife's) does not exist on CP1. In NFSv4, an unknown ID becomes user nobody. In NFSv3, is stays the same, not mapped to a username.

Mapping headaches and other issues could be solved by exporting with NFSv3 style. NFSv4 is only useful for complex situations which is never the case at home. Here is the export line I suggest:
> /media/Ubuntu_Data_Backup/Data 192.168.1.0/24(async,anongid=1000,all_squash,no_subtree_check,anonuid=1000,insecure,rw)
The ID here - 1000 - should match the ID of the main user on CP2. Use command 'id' in the terminal to get it. This will force the remote users to be seen as the local main user of CP2, gaining the same access privileges. If you want to really image the filesystem on CP2 and avoid spoofing the UID, say for backup purposes, you will have to enable root access in the export and do everything with sudo from CP1:
> /media/Ubuntu_Data_Backup/Data 192.168.1.0/24(async,no_root_squash,no_subtree_check,insecure,rw)
You client's fstab entry for the share should be:
> cp2.local:/media/Ubuntu_Data_Backup/Data /mnt nfs _netdev,vers=3 0 0
Hope this helps!

---

### Post by cscj01 on 2013-02-18
> **LewisTM said:**
> The first problem sounds like an ID mismatch problem, where the USB drive's owner UID (your wife's) does not exist on CP1. In NFSv4, an unknown ID becomes user nobody. In NFSv3, is stays the same, not mapped to a username.

Mapping headaches and other issues could be solved by exporting with NFSv3 style. NFSv4 is only useful for complex situations which is never the case at home. Here is the export line I suggest:

The ID here - 1000 - should match the ID of the main user on CP2. Use command 'id' in the terminal to get it. This will force the remote users to be seen as the local main user of CP2, gaining the same access privileges. If you want to really image the filesystem on CP2 and avoid spoofing the UID, say for backup purposes, you will have to enable root access in the export and do everything with sudo from CP1:

You client's fstab entry for the share should be:

Hope this helps!

I used your second export example because you mentioned doing backups, and that is the only reason I want the share (with restores of data if so required).

I changed my client fstab as you suggested.

All seemed fine after rebooting (perhaps I could have restarted things, but I chose to reboot), and I could browse to /mnt with Nautilus and see all my folders and files.  Then I ran luckyBackup sucessfully.

After I ran luckyBackup, I tried to browse to /mnt with Nautilus, and there is nothing there.  Here is the result of df -h:```
df -h
Filesystem                                Size  Used Avail Use% Mounted on
/dev/sdc2                                 421G  176G  225G  44% /
udev                                      2.9G  4.0K  2.9G   1% /dev
tmpfs                                     1.2G  1.1M  1.2G   1% /run
none                                      5.0M     0  5.0M   0% /run/lock
none                                      2.9G   80K  2.9G   1% /run/shm
/dev/sdb1                                 1.4T  873G  525G  63% /media/Data
/dev/sda1                                  31G   23G  8.0G  75% /media/sda1
/dev/sdc1                                  31G   20G   12G  64% /media/C48C88E98C88D6F8_
/dev/sdc2                                 421G   89G  311G  23% /media/b61632e9-7186-4ec9-9e4c-214c01d39a4e
/dev/sr1                                  286M  286M     0 100% /media/314 Reunions
cp2.local:/media/Ubuntu_Data_Backup/Data  1.4T  869G  529G  63% /mnt

```It shows the share still mounted, but when I browse to /mnt, it has no files or folders.  If I do an ls, I have ```
ls
ls: cannot access $RECYCLE.BIN: Stale NFS file handle
ls: cannot access GMail Signature.html: Stale NFS file handle
ls: cannot access MySQLDB: Stale NFS file handle
ls: cannot access Office10: Stale NFS file handle
ls: cannot access RECYCLER: Stale NFS file handle
ls: cannot access RR Signature.html: Stale NFS file handle
ls: cannot access Service Tags.txt: Stale NFS file handle
ls: cannot access System Volume Information: Stale NFS file handle
GMail Signature.html  Office10      RR Signature.html
My Documents          $RECYCLE.BIN  Service Tags.txt
MySQLDB               RECYCLER      System Volume Information

```What is happening?

---

### Post by cscj01 on 2013-02-18
So, after being away from my computer for 6 hours or so, I decided to browse my /mnt directory again.  Glory be!  There are my shares.  The file handles are no longer stale as indicated by this:```
ls
GMail Signature.html  Office10      RR Signature.html
My Documents          $RECYCLE.BIN  Service Tags.txt
MySQLDB               RECYCLER      System Volume Information
```And I did nothing to change the situation.

Is this normal behavior for NFS shares?  For what reason are the handles going stale, and where are the stale file handles being refreshed?  Is this more likely a server side issue or client side?

---

### Post by LewisTM on 2013-02-18
I've never experienced stale file handles and I doubt it's common on NFS shares, although they do seem to happen. It's probably a server-side problem. The server would "stop" serving these files momentarily. Perhaps it has something to do with your USB drive, maybe it has a powersave mode which would make the files unavailable to the NFS server. You could test this by exporting a directory residing on you hard drive. 

It's just speculation, Google might be of better help :)

---

### Post by cscj01 on 2013-02-18
> **LewisTM said:**
> I've never experienced stale file handles and I doubt it's common on NFS shares, although they do seem to happen. It's probably a server-side problem. The server would "stop" serving these files momentarily. Perhaps it has something to do with your USB drive, maybe it has a powersave mode which would make the files unavailable to the NFS server. You could test this by exporting a directory residing on you hard drive. 

It's just speculation, Google might be of better help :)
Thank you for the help.  I'll try to do some research on the USB drive and stale NFS handles.  I'll post what I find if anything of value.

---

### Post by cscj01 on 2013-03-04
Since I've found no other information of value about this issue, I'll mark this thread as solved because the issue has not re-appeared.  Everything continues to run smoothly so far.

---

### Post by cscj01 on 2013-03-04
:confused:  Okay, I surrender.  How do I mark this thread as solved with this new layout?  Thread tools no longer has that option.  I've looked all over the page, but I cannot find an option to mark it as solved.  Anyone care to help?

---

### Post by QIII on 2013-03-04
The script that used to do that does not work with vB4.  Normally, you could just use the thread tools to modify the thread title and add it, but you can only edit your posts for 7 days (an anti-spam measure).

I edited the title for you.

---

### Post by cscj01 on 2013-03-04
Thank you.

---

