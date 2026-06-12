---
title: "[SOLVED] Permissions problems: chown/chgrp/chmod"
date: 2007-11-26
forum: General Help
---

### Post by cygnine on 2007-11-26
I've a problem I just don't understand. I thought I knew the basics about permissions on these filesystems, but I guess I'm wrong:

I had Ubuntu 6.10 installed on my machine earlier. I have a vfat partition which I keep some personal files on. I had been backing these up using rsync (to another vfat drive). When I upgraded to 7.10, rsync gave me crazy chown and chgrp errors. Now I've tried to get to the core of the problem, and what I figured out is that on my original vfat partition, I cannot chown (or sudo chown/chgrp/chmod) any files on the vfat partition. (vfat doesn't do permissions, right? Fine.) 

Well now I'm guessing the distro upgrade changed some permissions on the vfat partition (???), and when I try to backup, rsync can't update the permissions on the backup drive, and it barfs lots of stuff about that to the terminal. sudo rsync does not work. I cannot reclaim the files on the vfat partition as mine because sudo chown does not work. How do I get around this? 

Here's another fun question: the vfat partition in question belongs to root: plugdev. Now if I run

```
cat /etc/passwd | grep plugdev
```

nothing is returned. Does that mean that the group plugdev doesn't exist? What does that mean? Help!!!!

---

### Post by nick_h on 2007-11-26
plugdev is a group so try:
```
cat /etc/group | grep plugdev
```
You will need to change the permissions on your FAT partition by changing the mount options in your /etc/fstab file.

---

### Post by cygnine on 2007-11-26
Thanks for the quick reply.

Yes, you are right, plugdev is a group (duh), so I should've done cat /etc/group instead. So yes, that group exists and gives me peace of mind. (Also, I'm a member of said group.)

However, now I've got some questions:
1.) I can find out how to get fstab to allow any user to mount the partition, and how to get it to assign a certain user and group as owner:group. Now suppose I change my partition to be owned by me:mygroup. Will this fix my rsync problem? rsync will still try to change permissions, right? (especially now that I've changed permissions on my files).

2.) Why did this change in rsync behavior happen in the first place? I *think* it has to do with my distro upgrade, but I can't really tell, and I don't know how to check.

---

### Post by nick_h on 2007-11-26
1. To allow any user to mount the filesystem use the *user* option.  To set the owner and group use the *uid* and *gid* options.  For permissions use the *umask* option.

Type:
```
man mount
```
for details on the mount options.

2. You might need to change the options for rsync to prevent assigning permissions.  What errors are you getting?

---

### Post by cygnine on 2007-11-26
1.) Actually, I already know how to mount a filesystem and assign default permissions (in fact, I've already done it). But my question was more along the lines of: files on my current backup have ownership me:root. I've just now mounted my local FAT partition to have default ownership me:me. Thus, when I rsync, I think it's still going to give me problems because for some crazy reason I can't change permissions on my backup FAT drive.

And in fact, if I cd into to my backup FAT drive and type in 
```
chgrp me somefile
```
chgrp comes back and tells me the operation is not permitted. sudo'ing it doesn't change the outcome. And this all happens despite the fact that the ownership of somefile is me:root.

I'm aware that permissions don't mean anything on FAT partitions, but I just don't want rsync to barf at me, which brings me to:

2.) A typical rsync error I get is 

```
rsync: chgrp "/media/WD120/backup/work/papers/rbm" failed: Operation not permitted (1)

```

This error is repeated x times, where x is the number of files I'm trying to back up (which is a heckuvalot). 

I'm currently running 
```
rsync -av --delete stuffstuffstuff backuplocation
```
Since you mentioned the options, I looked up -a (archive), and it's the same as -rlptgoD. Now, -pgo preserves permissions, group, and owner (respectively). I just ran rsync -rltDv, and there were no errors, which I guess fixes my problem. Thanks!

Given that I'm backing up a FAT partition to a FAT drive, am I losing anything by not syncing with the -pgo options?

---

### Post by nick_h on 2007-11-26
> **cygnine said:**
> Given that I'm backing up a FAT partition to a FAT drive, am I losing anything by not syncing with the -pgo options?

No, the permissions are not being saved anyway.  The permissions are only assigned when you mount the drive.

If you wanted to preserve permissions you could use tar instead, but I assume you are using rsync because you don't want to backup all the files that have not changed.

---

