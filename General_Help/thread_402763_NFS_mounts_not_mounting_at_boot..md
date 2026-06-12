---
title: "NFS mounts not mounting at boot."
date: 2007-04-06
forum: General Help
---

### Post by rcrook on 2007-04-06
Hi all,

got a nutty one. I just updated the nfs mounts on my laptop to NFSv4. I also cleaned up my fstab changing the /dev/sd?? tags to UUID tags. 

Unfortunately the nfs mounts (V4 or V2) don't seem to want to mount at boot anymore. 

After a lot of messing around this is what I have determined.

1. mount -t nfs,nfs4 -a will work when run manually. (even with out the "auto" in fstab (I tried it in and out)

2. all the local mounts work ok. IE: only the nfs mounts are ignored.

3. there is some weirdness with the version 2 nfs mount not showing up in /proc/mounts. Thus making the system confused as to if it is mounted or not. I can actually see files on the remote system but df and umount -t nfs -a doesnt seem to see it. No clue.

4. if I remove the "noproc" from the  
 mount -a -v -t noproc,nfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs
line in mountall.sh (/etc/init.d/) the script will mount all the nfs mounts correctly when run. If I leave it in it seems to ignore them.

Here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system>                              <mount point>    <type>      <options>                                                      <dump><pass>
proc                                         /proc            proc        defaults                                                            0     0
# Root = /dev/sda2
UUID=e9c33b9a-7625-4da8-b69b-ed94721ca711    /                ext3        nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid       0     1
# Home = /dev/sda4
UUID=1fc45a97-7687-4ca8-8757-77a5a0cf3f35    /home            xfs         nouser,defaults,atime,auto,rw,dev,exec,suid                         0     2
# Winxp = /dev/sda1
UUID=E4A4CEB5A4CE898E                        /local/winxp     ntfs-3g     defaults,nls=utf8,umask=007,uid=1000,gid=1000,auto,rw,nouser        0     0
# NFS Mounts
trinity:/public                              /remote/public   nfs4        bg,intr,soft,rsize=32768,wsize=32768                                0     0
trinity:/shared                              /remote/shared   nfs4        bg,intr,soft,rsize=32768,wsize=32768                                0     0
trinity:/priv                                /remote/priv     nfs4        bg,intr,soft,rsize=32768,wsize=32768                                0     0
trinity:/rcrook                              /home/rsc        nfs4        bg,intr,soft,rsize=32768,wsize=32768                                0     0
phoenix:/net/publish                         /remote/publish  nfs         bg,intr,soft,nfsvers=2,rsize=32768,wsize=32768                      0     0
# Removable Media
/dev/scd0                                    /media/cdrom0    udf,iso9660 user,atime,noauto,rw,dev,exec,suid                                  0     0
/dev/sdb1                                    /media/usb       auto        user,atime,noauto,rw,dev,exec,suid                                  0     0
# swap = /dev/sda3
UUID=bb0e94de-4729-4fd7-9c89-8cf28126f0ef    none             swap        sw                                                                  0     0

```

any help would be appreciated.

Thanks in advance

Randall Crook

---

### Post by kidders on 2007-04-07
> **rcrook said:**
> if I remove the "noproc" from the  
 mount -a -v -t noproc,nfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs
line in mountall.sh (/etc/init.d/) the script will mount all the nfs mounts correctly when run.This is what you would expect, since removing the "no" along with the "noproc" turns the mount command into an instruction to mount network filesystems, rather than a specific instruction *not* to.

I've seen this issue crop up on occasion. I can't help wondering if it has something to do with the order in which things are happening at boot.

---

