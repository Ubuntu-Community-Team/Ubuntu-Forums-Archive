---
title: "External Hard Drive not detected"
date: 2007-12-28
forum: General Help
---

### Post by Espy1988 on 2007-12-28
I have a Seagate 500GB External Hard Drive that is in NTFS.  It uses USB and when i plug it in it turns on and everything.  But nothin shows up on my desktop or anywhere else.  My flash drives work fine they show up on my desk top but this hard drive doesn't.  I Sudo fdisk and got this

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

so it seems like it detected it.  I have no idea how to access it though

---

### Post by stijngysemans on 2007-12-28
Have you ever installed ntfs 3G manually and edited the fstab files manually?

---

### Post by Espy1988 on 2007-12-28
I have no idea so i don't think so.  How do I do that?  Will it effect the data in my hard drive?

---

### Post by stijngysemans on 2007-12-28
Ok, then this ain't the problem.
What you can do is manually mount the hard drive.

go to the terminal
```

mkdir /media/myHD
mount /dev/sdc/ /media/myHD

```
What it should do: mount the hard drive to /media/myHD so you can access it from their. (the /dev directory only lists your hardware on a lower level).

---

### Post by vanadium on 2007-12-28
The drive should in principle mount automatically. It won't if the file system is not "clean". That is possible if the drive was connected while you hibernated Windows, or if you did not properly disconnect the drive. Therefore, first of all start Windows, have the drive checked, and disconnect the drive properly.

If you attempt the manual mount suggested by stijngysemans then that is fine, but do post the eventual error messages here: they can give a hint about the problem and probably will confirm what I said above. The command should be run as root, however.

---

### Post by TheMann00 on 2007-12-28
> **stijngysemans said:**
> Ok, then this ain't the problem.
What you can do is manually mount the hard drive.

go to the terminal
```

mkdir /media/myHD
mount /dev/sdc/ /media/myHD

```
What it should do: mount the hard drive to /media/myHD so you can access it from their. (the /dev directory only lists your hardware on a lower level).

I have a similar issue- with your code above, where did you come up with the "/dev/sdc" -- I can't find a way to know what's out there.  I'm coming from Unix and windows- so I know exactly what I want to do, just not the command for it ;)

---

### Post by TheMann00 on 2007-12-28
> **TheMann00 said:**
> I have a similar issue- with your code above, where did you come up with the "/dev/sdc" -- I can't find a way to know what's out there.  I'm coming from Unix and windows- so I know exactly what I want to do, just not the command for it ;)

Answered my own question: posting here for others.
[INDENT]sudo fdisk -l[/INDENT]
Gave me all the info I needed!

---

### Post by Espy1988 on 2007-12-28
I tried what you said and it says i don't have permission to write in that folder so i can't make that directory.  I always dissconnect my hard drive safely from windows.  But just in case i did it again and got nothing.  I tried the second command just for fun and got "mount: only root can do that"

Any ideas? Thank you

---

### Post by TheMann00 on 2007-12-28
> **Espy1988 said:**
> I tried what you said and it says i don't have permission to write in that folder so i can't make that directory.  I always dissconnect my hard drive safely from windows.  But just in case i did it again and got nothing.  I tried the second command just for fun and got "mount: only root can do that"

Any ideas? Thank you

You have to put sudo in front of those commands.  Anytime you want to do something as root (the end-all-be-all system administrator) you type sudo first.  This will emulate yourself as being logged in with the root account.

```
sudo mkdir /media/myHD
sudo mount /dev/sdc/ /media/myHD
```

---

### Post by TheMann00 on 2007-12-28
Here is my new problem: I came to this thread to try and get some drives mounted.  I have a 500GB ntfs that is IDE, and a 250GB Seagate FreeAgent ntfs.

I can right click on the IDE drive and mount it.  I ran *sudo fdisk -l* and got the following:
[INDENT]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5553dc55

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30401   244196001    7  HPFS/NTFS
[/INDENT]

So then I 
```
sudo mkdir /media/FreeAgent
sudo chmod 777 /media/FreeAgent
sudo mkdir /mnt/MediaDrive
sudo chmod 777 /mnt/MediaDrive
```

And wrapped it up with editing fstab with the following code:
[INDENT]#FreeAgent USB Drive
/dev/sdf1 /media/FreeAgent ntfs defaults 0 0

#MediaDrive on IDE Cable
/dev/hdd1 /mnt/MediaDrive ntfs defaults 0 0[/INDENT]

When I reboot, the FreeAgent shows up as expected, the IDE drive does not.  It isn't even listed under places>computer - as it was before when I could manually mount.  I commented out the last line of fstab (*/dev/hdd1 /mnt/MediaDrive ntfs defaults 0 0*) and it shows up in places>computer again, and is manually mountable once more.  I did also change /mnt to /media, did all the chmod stuff, and same issue.  so I changed it back, since it is a permanently attached drive.  **_Ideas?_**

---

### Post by Espy1988 on 2007-12-28
Aright did that and it said "you must specify the file system type"

michael@michael-desktop:~$ sudo mount /dev/sdc/ /media/myHD
mount: you must specify the filesystem type

---

### Post by Espy1988 on 2007-12-29
bump

---

### Post by TheMann00 on 2007-12-30
> **Espy1988 said:**
> Aright did that and it said "you must specify the file system type"

michael@michael-desktop:~$ sudo mount /dev/sdc/ /media/myHD
mount: you must specify the filesystem type

I see what you are saying, and I am stumped also.  The drive I am having issues with- I can mount it via the GUI, but not in the terminal.  Is there a reason that a USB drive would mount this way, and an IDE would not?

---

### Post by vanadium on 2007-12-30
> 
Aright did that and it said "you must specify the file system type"

michael@michael-desktop:~$ sudo mount /dev/sdc/ /media/myHD
mount: you must specify the filesystem type


Since your partition is /dev/sdc1, you must specify that rather than /dev/sdc/

---

### Post by Espy1988 on 2007-12-30
Thank you so much it worked!  Thanks to everyone!

---

