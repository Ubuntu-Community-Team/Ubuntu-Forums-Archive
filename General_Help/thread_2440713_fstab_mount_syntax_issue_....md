---
title: "fstab mount syntax issue ..."
date: 2020-04-14
forum: General Help
---

### Post by michael351 on 2020-04-14
I have an external hard drive which I connect on and off. I would like to boot the system and have it ignore the drive if it is not there.

I edited fstab and put this entry:

UUID=88C2D23DC2D22F66 /media/htpc ntfs  auto,nofail,noatime,rw,user     uid=1000,gid=1000,dmask-022,fmask=133   0       2

I get a syntax error at this line: "1 parse error at line 16"

What is my error? all spaces are tabs in the above example.
My goal is to have a successful boot whether the disk is connected or not - and if connected to mount it.

---

### Post by westie457 on 2020-04-14
Can we have a better clue please?
Post the output of ```
cat -n /etc/fstab
```

---

### Post by michael351 on 2020-04-14
1  # /etc/fstab: static file system information.
     2  #
     3  # Use 'blkid' to print the universally unique identifier for a
     4  # device; this may be used with UUID= as a more robust way to name devices
     5  # that works even if disks are added and removed. See fstab(5).
     6  #
     7  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
     8  # / was on /dev/sda8 during installation
     9  UUID=24af3e43-a0b1-4376-87b7-7c0cfad2d050 /               ext4    errors=remount-ro 0       1
    10  # swap was on /dev/sda7 during installation
    11  UUID=b93d264a-92c0-4646-90c9-052cc0f12021 none            swap    sw              0       0
    12
    13  # Mount USB drive /dev/sdb1
    14  #UUID=88C2D23DC2D22F66 /media/htpc ntfs uid=1000,gid=1000,dmask=022,fmask=133 0 0
    15  #Changed Mount entry for USB drive (added 7 Jan 2018)
    16  UUID=88C2D23DC2D22F66 /media/htpc ntfs  auto,nofail,noatime,rw,user     uid=1000,gid=1000,dmask-022,fmask=133   0       2

---

### Post by SeijiSensei on 2020-04-14
It appears there is a space, not a comma, between "user" and "uid" .

---

### Post by michael351 on 2020-04-14
Thanks - when I put a comma between "user" and "uid", I get the errors below when I verify fstab:

sudo findmnt --verify
/media/htpc
   [E] unreachable on boot required target: No such file or directory
   [E] unreachable on boot required source: UUID=88C2D23DC2D22F66

0 parse errors, 2 errors, 0 warnings

---

### Post by gsahli on 2020-04-14
I think you should run sudo blkid again to be sure you have the correct UUID.

---

### Post by TheFu on 2020-04-14
Options cannot have spaces. Period.
The '-' after the dmask is wrong too.

auto,nofail,noatime,rw,**user uid=**1000,gid=1000,dmas**k-0**22,fmask=**133**

The fmask is really odd too.   Try 0002 instead - for both the dmask and fmask.   But if the partition is for an NTFS disk, 

i has a usb NTFS partition that is sometimes there and sometimes not.  The automount options are:
```
nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```
i don't mount using the fstab for that storage, but the options should be the same, mostly.  No spaces, no dashes.

---

### Post by GhX6GZMB on 2020-04-14
Your UUID looks really odd.

---

### Post by TheFu on 2020-04-14
> **ml9104 said:**
> Your UUID looks really odd.

Looks like an NTFS UUiD to me.

---

