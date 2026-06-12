---
title: "NFS 'Permission denied' Only when Copying Files to Share"
date: 2015-09-27
forum: General Help
---

### Post by cjsheets on 2015-09-27
Hi Guys. After several hours of searching this issue has me stumped.

I have a basic NFS setup between an updated Ubuntu Server and xUbuntu desktop (pretty much per Community wiki). Somehow I can mount, read, delete, create and update files on the share but I cannot copy ("~$ cp xx yy") files to it.

**Desktop Actions:**
[FONT=Fixedsys][COLOR="#008000"]desktop:~$[/COLOR] touch /mnt/server/create-file
[COLOR="#008000"]desktop:~$[/COLOR] touch copy-file
[COLOR="#008000"]desktop:~$[/COLOR] ls -lan
drwxr-xr-x 32 1000 1000 4.0K Sep 27 13:28 ./
drwxr-xr-x  3    0    0 4.0K May 25 19:59 ../
-rw-rw-r--  1 1000 1000    0 Sep 27 13:28 copy-file
[COLOR="#008000"]desktop:~$[/COLOR] cp copy-file /mnt/server/
[COLOR="#FF0000"]cp: cannot create regular file &#8216;/mnt/server/copy-file&#8217;: Permission denied[/FONT][/COLOR]

**Server Result:**
[FONT=Fixedsys][COLOR="#008000"]root@server:/export/nfs#[/COLOR] ls -lan
drwxrwxrwx  18 1000 1000      4096 Sep 24 16:51 .
drwxr-xr-x   3     0     0      4096 Sep 20 10:15 ..
----------   1  1000  1000         0 Jan 11  1970 copy-file
-rw-rw-r--   1  1000  1000         0 Sep 27 13:28 create-file[/FONT]

'rm /mnt/server/c*' from the client successfully removes both files. uid and gid on both server and client = 1000. Even in subdirectories created by the client the issue persists.

Some configuration files...

**Client**
*/etc/fstab*
```
192.168.2.14:/nfs /mnt/server nfs rw 0 0
```

**Server**
*/etc/exports*
```
/export         192.168.2.0/24(rw,fsid=0,no_subtree_check,sync)
/export/nfs    192.168.2.0/24(rw,fsid=1,no_subtree_check,sync)

```


Does anyone have an idea why file creation would work while copying fails? Any tips or assistance would be greatly appreciated.

---

### Post by TheFu on 2015-09-27
Do the uid/gid for both systems match? These are  the numbers. The names don't need to match, but numbers do.  Use 'id' to check this on each of the systems.

---

### Post by cjsheets on 2015-09-27
Yep, they sure do (or at least seem to).

[FONT=Fixedsys][COLOR="#008000"]desktop:~$[/COLOR] id
uid=1000(chad) gid=1000(chad) groups=1000(chad),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),115(lpadmin),131(sambashare),135(libvirtd)

[COLOR="#008000"]chad@server:/$[/COLOR] id
uid=1000(chad) gid=1000(chad) groups=1000(chad),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),110(sambashare)[/FONT]

---

### Post by TheFu on 2015-09-28
fsid=1?
fsid=0?

I don't use those.  Also, in the fstab, might want to specify ver=3.  Here are my options:
-fstype=nfs,hard,intr,rw,async,vers=3

---

### Post by cjsheets on 2015-09-28
I gave those options a try and received an error message. Researching the error it looks like because I'm exporting a fuse-mounted filesystem (mergerfs, similar to mhddfs or aufs) I'm required to use nfsv4.

I've been playing with different nfs4 mount options to no avail. I'll try exporting a non-fuse-mounted file system and see how that goes.

---

### Post by TheFu on 2015-09-28
Do you have Kerberos setup? Doesn't NFSv4 require it?  FUSE?  Yuck.

---

