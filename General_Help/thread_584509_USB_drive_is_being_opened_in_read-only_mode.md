---
title: "USB drive is being opened in read-only mode"
date: 2007-10-21
forum: General Help
---

### Post by Oberiko on 2007-10-21
Hello.

On 7.04, I'm trying to mount an external hard drive (NTFS), but it keeps coming up as a Read-Only file system.  In permissions, the owner and group are both root, and the only permission available is that the owner can view contents.

How can I get this to work properly (ie, a readable/writable hard drive)?  It's empty, so I don't mind reformatting it.

---

### Post by Whiffle on 2007-10-21
Do you have ntfs-3g installed yet?  Thats the first step to making it read/writeable.  Next we'll have to edit your /etc/fstab so that users can read/write it.

---

### Post by Oberiko on 2007-10-21
Hi, 

Yes, I have ntfs-3g installed

---

### Post by Oberiko on 2007-10-21
Sorry, which file am I editing now?

---

### Post by Whiffle on 2007-10-21
Being an old fart used to the old ways of linux, this is the way i'd do it, although you might poke around the howto's a bit and see if there is a newer better way.

Two things need to be done,
1) Make a mount point.
Since each device needs a directory to be mounted to, the directory has to be there in the first place.  I would do something like this:

```

sudo mkdir /mnt/externaldrive

```

2) You'll need to edit /etc/fstab.  

```

gksudo gedit /etc/fstab

```

The fstab is the file that tells linux where all the drives are, where they are to be mounted, and how to do it.   You'll need to add a line like this:


```

/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8,users   0    0

```

The first bit is the device, like /dev/sda1.  The sd tells that its a scsi device, the a says it is the first one, and the 1 points to the first partition on that device.  The next bit is the mount point, /mnt/externaldrive in our case.   The next tells it what kind of filesystem, in our case, ntfs-3g.  Next are different attributes it has, usually defaults is all you need, but we're going add users to allow users to access it.  The locale=en_US.utf8 tells it what kind of characters to expect.  Finally, the two 0's tell whether or not to fsck the drive at boot.  More info on fstab can be found with

```

man fstab

```


After you save the newly edited fstab, you should be able to mount it by hand with

```

mount /mnt/externaldrive

```

It may complain that its already mounted somewhere else, in which case you could do 
```

sudo umount /dev/<device>

```

I hope thats all right... its been a while since I've actually had to do this.  That will change on tuesday though when my new 500GB drive gets here :D

---

### Post by DagMan on 2007-10-21
in step 2 you overlooked the change from /mnt to /media
so as you have it now.
```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8,users   0    0
```
should be 
```
/dev/<your partition>     /mnt/externaldrive     ntfs-3g     defaults,locale=en_US.utf8,users   0    0
```

Indeed confusing, like you say if you've used linux long enough to have wondered why /media started to be the convention in ubuntu.

---

