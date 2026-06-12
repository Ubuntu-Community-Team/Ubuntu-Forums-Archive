---
title: "access control lists"
date: 2007-01-07
forum: General Help
---

### Post by firebadger on 2007-01-07
Has anybody got access control lists working.  I'm trying to use them to grant access to a directory to specific users without needing complex group memberships.

I modified my fstab file, and it looks like they should be working...  this is the info mount returns about the drive...

```
/dev/hda1 on / type ext3 (rw,acl,errors=remount-ro)
```

I ran the following to set the permissions (and defaults), but the user can't access

```
setfacl -R -d -m user:evonne:rx photos

setfacl -R  -m user:evonne:rx photos
```

Any insights anybody?

---

### Post by teddy_baykard on 2007-10-04
Hi firebadger, please try to move your 'photos' directory to another partition except  / or  /boot. Also, ACL cannot be set to /swap partition of course :D
reconfigure option "rw,acl" for suitable partition in /etc/fstab, then remount it.

for example in your case:
$ sudo vim /etc/fstab
   /dev/sda5  /data  ext3  (rw,acl,errors=remount-ro)      0          2

$ sudo -v -o remount /dev/sda5
   /dev/sda5  on   /data  type  ext3  (rw,acl,errors=remount-ro)

Then you can set permissions (file/folder) as you wish. Hope that's usefull.

---

### Post by firebadger on 2007-10-08
Could be... I'll try again at some point. ..Thanks.

I didn't know there was any restriction on the partitions you could run them on.  Do you have any more info on that?

---

### Post by prezbedard on 2007-10-27
I'm was trying to learn acls in linux

so I installed acl

I created a test dir support under /

I then entered the following line in /etc/fstab

```
 /dev/hda2 /support ext3 rw,acl,errors=remount-ro 0 1           
```

I then entered a mount command to remount the change

I was able to use acl but discovered I some how mounted the whole file system under /support

How can I undo this change and just have acl support on /support ?

Thanks!!

---

### Post by prezbedard on 2007-10-27
ok I was able to unmount the file system from /support and keep acl support

any idea what I did that caused the whole file system to mount instead of just remounting the support dir for acl support to take affect?

one other thing I ran getfacl and the changes I mad took affect which were rwx for my account however I can only do any kind of action from the cli and not in the gui on the dir support but on the subfolder in support I created I can modify it within the gui.

Thanks!!

---

