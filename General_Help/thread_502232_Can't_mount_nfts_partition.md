---
title: "Can't mount nfts partition"
date: 2007-07-16
forum: General Help
---

### Post by TheOtherLinuxFreak on 2007-07-16
I am trying to mount a nfts partition and i get this in the terminal. 

```
root@aw:~# mount /dev/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
```

What do I do now?

Edit: I'm not dual booting windows and ubuntu.

---

### Post by merlinus on 2007-07-16
Run ntfsfix on the partition, e.g. sudo ntfsfix /dev/hda6

-merlin

---

### Post by TheOtherLinuxFreak on 2007-07-16
Now I get this:
```
root@aw:~# mount /dev/sda2
Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
```

---

### Post by splintercellguy on 2007-07-16
Stick in the -o force option.

---

### Post by merlinus on 2007-07-16
mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

Does this work?

-merlin

---

### Post by stchman on 2007-07-16
> **TheOtherLinuxFreak said:**
> I am trying to mount a nfts partition and i get this in the terminal. 

```
root@aw:~# mount /dev/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
```

What do I do now?

Edit: I'm not dual booting windows and ubuntu.

I have a procedure for mounting NTFS partitions.  I am assuming that this NTFS partition is a Windows partition.  I recommend that you boot into Windows and crun a chkdsk /f on all NTFS drives.

Once that is done then follow my procedure:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by TheOtherLinuxFreak on 2007-07-16
> **merlinus said:**
> mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

Does this work?

-merlin

Now I get this:

```
root@aw:~# mount -t ntfs-3g /dev/sda2 /media/sda2 -o force
WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 (backup)

```

stchman, I'm not dual booting ubuntu / windows.  I'm only using ubuntu.

---

### Post by merlinus on 2007-07-16
Did you try running ntfsfix on the partition?

Also, since you are not running windows, why not format the disk as ext3?

Finally, if it is an external drive, perhaps you can take to a friend's house and run

chkdsk <drive letter>: /f

from windows.

-merlin

---

### Post by TheOtherLinuxFreak on 2007-07-16
I did Try using ntfs fix but it didn't work. Its a partition. If I reformat to ext3, will the data be lost?

---

### Post by merlinus on 2007-07-16
Just to be clear --

You ran

```

sudo ntfsfix /dev/sda2

```and it did not solve the problem?

And yes, if you format it to ext3, all data will be lost.

-merlin

---

### Post by TheOtherLinuxFreak on 2007-07-16
yes I ran exactly that. It did not solve the problem. i really want to keep the data. what if i put it (the hd) in a windows pc and ran chdsk?

---

### Post by merlinus on 2007-07-16
IIRC, you cannot go back to fat32 without losing your data as well.... it only works going from fat32 to ntfs.

-merlin

---

### Post by TheOtherLinuxFreak on 2007-07-16
so should I put the hd in a windows pc and run  chkdsk on it?

---

### Post by merlinus on 2007-07-16
If possible.  The /f switch (chkdsk <drive letter>: /f ) will try to fix any errors automatically.

Good luck!

-merlin

---

### Post by TheOtherLinuxFreak on 2007-07-16
I put the hd in my windows pc and ran chkdsk on it and now it works fine. Thanks for your help!

---

