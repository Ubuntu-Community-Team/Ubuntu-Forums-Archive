---
title: "[SOLVED] Problems with permissions after formatting USB pendrive"
date: 2007-08-25
forum: General Help
---

### Post by PmDematagoda on 2007-08-25
I tried formatting my USB pen drive this way :

To format an external drive for example, you would first have to figure out the device name

df -k /media/disk

That *should* have only two lines of output and should looks something like this:

--------------------

Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda1 112420772 83649824 23060244 79% /

---------------------

The "/dev/sda1" portion is what we care about, though your USB drive will probably have a number like "/dev/sdc1".

So, first, become root:

--------------
sudo -s
---------------

Then, unmount the drive:

---------------
umount /media/disk
----------------

Then create the filesystem:

------------------
mkfs.ext3 devicename

( in this case mkfs.ext3 /dev/sdf1)
-----------------

Again, please be careful that you have the device that is mounted on top of /media/disk. If the device is "sda", then it is almost certainly your internal disk, and that will break your PC.

Type the "sync" command twice (just to be sure that the blocks got flushed to disk):

---------------------------
sync
sync
----------------------------

And, if the drive hasn't already remounted itself, unplug it (or switch off) and plug back in. It should automatically come up.

sudo chown -R yourname /media/disk 

but when the format was finished i found that the file system was converted to ext3(Not a problem) and also that the owner of the drive was changed to the root which means that i can't do any changes to the drive or put any files to it or anything(This is the real problem), when i plug it into a windows system it detects the drive and allows files to be put into it(After reformatting the drive to NTFS). Does any one know how to solve the problem?Not necessarily the file system one as i fixed it with gnome partition manager and it was very interesting.

---

### Post by jamvegan on 2007-08-26
> sudo chown -R yourname /media/disk

This is the line that should have changed the ownership to you (assuming that you changed "yourname" to your actual username and "/media/disk" to the actual mountpoint of the drive).

---

### Post by PmDematagoda on 2007-08-26
I tried your method jamvegan, the output was:

```

pramod@pramod-desktop:~$ sudo chown -R pramod /media/Kingston128"(NTFS)"
chown: changing ownership of `/media/Kingston128(NTFS)/Shyama Liyanage.doc': Read-only file system
chown: changing ownership of `/media/Kingston128(NTFS)': Read-only file system
pramod@pramod-desktop:~$ 

```

After that i checked the USB pen drive it was still the same, I even unmounted it and mounted it again but the permissions weren't changed.:confused:

---

### Post by jamvegan on 2007-08-26
Sorry, I missed the part of your original post where you mentioned that Windows had reformatted the drive to NTFS.  As far as I know, Ubuntu always mounts NTFS filesystems read-only.  I think that there are ways to change that, but I do not know them, personally.

---

### Post by PmDematagoda on 2007-08-27
> II missed the part of your original post where you mentioned that Windows had reformatted the drive to NTFS

Sorry you misunderstood my statement, it means that i formatted my pen drive to NTFS using linux itself through Gnome partition editor, but it's nothing with the file system because i can read and write to my windows partition which is NTFS. The other thing is that even when i changed the filesystem to FAT 16, 32, and ext3, the drive remained read-only. The only way i can add files or delete files in the drive is using windows which has no problem with it, the thing is i want to add files  to the drive while in linux.:confused:

---

### Post by jamvegan on 2007-08-27
I just came across [this thread]("http://ubuntuforums.org/showthread.php?t=368366"), which may be of use to you?

---

### Post by PmDematagoda on 2007-08-28
Thanks jamvegan it solved my problem.:)

---

