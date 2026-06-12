---
title: "Advanced user account management"
date: 2013-02-08
forum: General Help
---

### Post by boas on 2013-02-08
Hi!
I am setting up an ubuntu server where several different users will have access via remote desktop.
I have set up some user accounts without root permissions, but I want to have more specifik control of the users rights:
*They must all have a defined amount of storage space available.
*They should have access to launch some programs but not others.
*They should only be allowed to see the content of their home folder.

I once came across a keyword to this more advanced control of user accounts in linux but I can't remember it? It was a different approach than the permission-to-folders-read-write-only-thing...

I guess there are allready threads discussing the matter, but I can't seem to find them. Any help is much appreciated!

---

### Post by schragge on 2013-02-08
> **boas said:**
> *They must all have a defined amount of storage space available.For this, look at [quota]("http://packages.ubuntu.com/quantal/quota") and [quotatool]("http://packages.ubuntu.com/quantal/quotatool").

---

### Post by boas on 2013-02-14
Thanks for that.

I have now tried 4 different quotatool tutorials without success... I even had to recover a damaged fstab and a system not booting up...
Anyway, the problems I am experiencing seems several fold. I want to enable quotas for some users on the internal hdd of my server.
The internal disks are named (output from blkid):
/dev/sda1: UUID="e3947630-2d20-4f1b-9d4e-049f3d0c05ee" TYPE="ext2"
/dev/sda5: UUID="DZ0z47-SysY-Gv7d-cgHw-m2Q1-r5eo-8nLFfI" TYPE="LVM2_member"
/dev/mapper/ubuntuserver-root: UUID="ecf4bcdd-5627-472e-83d3-9bbdaf341814" TYPE=            "ext4"
/dev/mapper/ubuntuserver-swap_1: UUID="e7aecde0-9d97-44d9-87b7-bf274838414e" TYP            E="swap"

My "main" partition, i.e. the one with the user home directories, is that sda1 or sda5? or should I use /ubuntuserver-root?

I tried to set up disk quotas on an external hdd to avoid messing things up. My /etc/fstab then looked like this:
/dev/sdb1       /          ext3    defaults,usrquota 0  2

After rebooting and calling quotacheck from the terminal, I got a "permission denied"-answer. Furthermore, it looked like the quotas were trying to be applied to the internal hdd.

In short: Anyone with a thorough guide on the use of quotatool with an ubuntu 12.04 server? Thanks in advance...

---

### Post by schragge on 2013-02-14
Your main (root) filesystem resides on logical volume */dev/mapper/ubuntuserver-root* that shares partition /dev/sda5 with another logical volume */dev/mapper/ubuntuserver-swap_1*

To see what /dev/sda1 is used for, type
```
findmnt /dev/sda1

```
I guess it's your boot partition.

---

### Post by boas on 2013-02-15
@Schragge, thanks again for your interest. I really appreciate it.

Yes, I used the /ubuntuserver-root, and tried to enable quotas thereon. However, after rebooting and calling the quotacheck -avug command, it says that no partitions are selected for quotas. I then installed webmin and tried a GUI-approach, but webmin says that it cannot find the quota.user database file. I have manually created the aquota.user and quota.user file in the root directory, so the files are there. Have anyone experienced something similar with 12.04? Or could it be the partition setup I'm using? 

...starting to look at other options for quotas...

-Boas

---

### Post by rnerwein on 2013-02-15
> **boas said:**
> Hi!
I am setting up an ubuntu server where several different users will have access via remote desktop.
I have set up some user accounts without root permissions, but I want to have more specifik control of the users rights:
*They must all have a defined amount of storage space available.
*They should have access to launch some programs but not others.
*They should only be allowed to see the content of their home folder.

I once came across a keyword to this more advanced control of user accounts in linux but I can't remember it? It was a different approach than the permission-to-folders-read-write-only-thing...

I guess there are allready threads discussing the matter, but I can't seem to find them. Any help is much appreciated!
hi
for this: *They should have access to launch some programs but not others.
i think you can use ACL --> [http://wiki.ubuntuusers.de/ACL](http://wiki.ubuntuusers.de/ACL)
for this: *They should only be allowed to see the content of their home folder.
see man rbash - but it is not realy restricted (if they know the folder and path they can see it)


ciao

---

### Post by lykwydchykyn on 2013-02-15
> **boas said:**
> 
*They should have access to launch some programs but not others.

Do you mean launch with sudo or just launch at all?  If you want to restrict which programs a sudo user can launch with sudo, see:
```

man sudoers

```
> 
*They should only be allowed to see the content of their home folder.

In what context?  SSH?  Samba? SFTP?  NFS?
> 

I once came across a keyword to this more advanced control of user accounts in linux but I can't remember it? 

Maybe SELinux or AppArmor?  These are Mandatory Access Control systems, that let you limit what a process can access on the system.  Ubuntu uses AppArmor, but I don't think it can be used to limit on a per-user basis.

---

