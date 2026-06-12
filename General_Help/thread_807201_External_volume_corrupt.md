---
title: "External volume corrupt"
date: 2008-05-25
forum: General Help
---

### Post by Warmask on 2008-05-25
I have an external USB hard drive with 2 ntfs volumes, 1 for music and one for movies.  I was transfering a couple of dvd isos to the movie volume and the computer froze. I left it be for little while, hoping it was just lag, but it would not come back.  I was forced to do a hard reboot.  When I restarted, i could access the volume, but there was an ISO image that didn't finish transfering, it was only 40mB.  It would not let me delete this file saying "Error "I/O error" while deleteing "/media/Mov...RIDESE.ISO". It also will not let me create any new folders or transfer any files.

I booted to Windows and it will open my Music volume, but it will not open my Movie volume saying that it is corrupt.

In ubuntu I can view my files and transfer them, so I am in the process of transferring them to my hard drive.

Is there a way to do a "check disk" in ubuntu?  Or is there another way to get my drive "uncorrupted"??

Please, any help is welcome.  Thank you.

---

### Post by Warmask on 2008-05-25
Well, aparently the 'fsck' command does not work on ntfs volumes.  Is there a way to check ntfs disk? will i have to physically put it in my computer and check it with vista? or am i gonna have to format the whole volume?

Thanks

---

### Post by nick_h on 2008-05-26
There is an *ntfsfix* program in the *ntfsprogs* package.

I would recommend that you use Windows to fix an ntfs partition though.

---

### Post by Warmask on 2008-05-27
Thank you, I will try that.

Windows does not recognize the partition. I don't know how to get it to check a USB partion when it does not recognize it.  It does however recognize the other partition on the same disk.  And I can still read the data on Ubuntu.  So I'm backing up what I can and I guess I will just wipe it.

I did notice while trying to transfer large (4gB) dvd isos to the hard drive from the usb hard drive, that it hangs endlessly after a little while of transfering. (Transfering ISOs to the external is what caused this problem in the first place)
My question:
Does Ubuntu have a hard time dealing with large files on a NTFS drive?

---

### Post by nick_h on 2008-05-27
> Does Ubuntu have a hard time dealing with large files on a NTFS drive?
I haven't read of any problems.  NTFS is does not have the 4GB file limit that FAT filesystems have.

---

