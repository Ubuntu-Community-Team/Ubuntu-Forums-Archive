---
title: "Problem with mount permissions"
date: 2007-05-18
forum: General Help
---

### Post by prankst3r on 2007-05-18
I have a permissions issue with an sshfs mount and am wondering what I need to do to resolve it. Basically I have a group called "fileshare" with a gid=1001. I want to make sure that members not in this group are not allowed to access to the sshfs mount.

Okay, that being said, I created a user called "testuser" and they are still able to access the mount. Here is my mount directory:

```
jeff@everest:/mnt$ ls -l
total 4
drwxr-xr-x 2 root root 4096 2007-05-18 10:47 document_share
jeff@everest:/mnt$ 

```

Now I will mount the share:

```
jeff@everest:/mnt$ sudo mount /mnt/document_share
jeff@everest:/mnt$ ls -l
total 4
drwxrwx--- 1 root fileshare 4096 2007-05-18 10:49 document_share
jeff@everest:/mnt$ 
```

As you can see, document_share has 770 permissions and is owned by root:fileshare

My main user "jeff" is a member of the fileshare group:

```
jeff@everest:/mnt$ id
uid=1000(jeff) gid=1000(jeff) groups=4(adm),6(disk),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(jeff),1001(fileshare)

```

I can access the mount (rw) with no problem:
```
jeff@everest:/mnt/document_share$ touch test
jeff@everest:/mnt/document_share$ ls -l test
-rw-r--r-- 1 jeff fileshare 0 2007-05-18 11:01 test
jeff@everest:/mnt/document_share$
```

Now I will switch over to my "testuser" user - note "testuser" is not a member of the "fileshare" group:

```
testuser@everest:/mnt$ id
uid=1002(testuser) gid=1003(testuser) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),104(scanner),120(fuse),1003(testuser)
testuser@everest:/mnt$ 
```

I can still access the mount (rw) even though my permissions should be denied for /mnt/document_share:

```
testuser@everest:/mnt/document_share$ touch test
testuser@everest:/mnt/document_share$ ls -l test
-rw-r--r-- 1 jeff fileshare 0 2007-05-18 11:04 test
testuser@everest:/mnt/document_share$ 

```

Here is my fstab configuration:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9035f9e7-1112-4dba-b749-c23d471a3bf6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=aaf565fb-1eb3-420e-977f-17f59183c684 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
sshfs#jeff@k2:/fileshare/paperport	/mnt/document_share	fuse	comment=sshfs,noauto,gid=1001,allow_other,reconnect,transform_symlinks 0 0
```

I have tried removing "allow_other" from the fuse option, but then there is no way to access the share from any user. Anyone have any suggestions?

---

