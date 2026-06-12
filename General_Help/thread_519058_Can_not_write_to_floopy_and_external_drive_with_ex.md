---
title: "Can not write to floopy and external drive with ext2"
date: 2007-08-06
forum: General Help
---

### Post by oldcpu on 2007-08-06
I can not write to floopy and external drive with ext2 unless I use sudo.  Why is that?  I can write fine if the external drive is formated in ext3.

---

### Post by RHTopics on 2007-08-06
It is probably a difference in the way they are being mounted.

Do a "mount' command and compare the difference between the ext2 mounted drive and the ext3 mounted drive.

Also look at your /etc/fstab file and see how it mounts the floppy drive.  Post your /etc/fstab file if you need more help.

Another thought is to look at your permissions on these drives.  If you set up the directories using sudo (under root permission), then only root would be able to write to them.  Changing the permissions to allow others to write to the directories/files would solve your problem.

---

### Post by oldcpu on 2007-08-06
How do I compare mount of the ext2 and ext3?  I mount the both the same way.

```
sudo mount /dev/sda1 /mnt
```

Never mind the floppy problem.  Found out that I can get it to mount with user permissions if I use fd0 instead of fd.

---

### Post by RHTopics on 2007-08-07
Okay, I have a better understanding how you are mounting your drives.  You are bypassing the use of the /etc/fstab file.

If you want to have write access for all users of the mounted drive, then try the following commands:

```
cd /mnt
sudo chmod +rwx *

```
This will give read, write, and execute access for all top (root level) files to all users who can access the mounted drive.

---

### Post by oldcpu on 2007-08-07
That would mess up the default permissions of some files as some are not meant to be written or excuted.

I do not think the files itselves are the problem, I think it is the drive.  Because I tried making and saving a file or folder within the ext2 drive, and it denies me as user.  As mentioned before, this does not happen if the FS is ext3.

Why does this happen?

---

### Post by RHTopics on 2007-08-07
Whether the drive is formatted as ext2 or ext3 in itself is not relevent to your problem.  The drive you have formatted as ext3 has its permission set at the root level to allow users other than root to write to the drive.

Try this on the ext2 drive and see if it allows write access to files in a directory

```
cd /mnt
sudo mkdir --mode a=rwx testdir
cd testdir
touch testfile

```
The touch command will create an empty file with the name of testfile.

Let me know what you get when try this.

---

