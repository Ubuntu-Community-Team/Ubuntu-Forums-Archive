---
title: "System fails to boot"
date: 2008-05-20
forum: General Help
---

### Post by puffyzacd on 2008-05-20
I seemed to screw up my system pretty badly yesterday. I was experiencing some very long boot times similar to what is described here: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/192845](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/192845)

It appeared to be a bug in udev that might be related to outdated rules files, but I wasn't able to determine which rules were causing the problem. Apparently this was a mistake, but I removed all the rules files (after backing them up) and reinstalled udev. Subsequent attempts to boot the computer failed (obviously, since there were no rules files in the /etc/udev/rules.d/ folder). But now, even after restoring all the backup rules files I am still unable to boot!

The system seems to load the kernel and the ubuntu splash screen comes up, but it doesn't get past "waiting for root partition" (the orange block moving left and right inside the progress bar).

Does anyone have any ideas of how to restore my system?

Thanks!

---

### Post by puffyzacd on 2008-05-20
I'd rather not reinstall my whole system because of this!

Anyone?

---

### Post by bingoUV on 2008-05-20
did you try reinstalling udev after restoring the rules?

---

### Post by lswest on 2008-05-20
check the permissions on the files you copied back over, it should be root for owner, root for group, read & write permissions for owner, and read for group and other.

---

### Post by puffyzacd on 2008-05-20
> **bingoUV said:**
> did you try reinstalling udev after restoring the rules?

I would try this, but I can't log in and so I'm not sure how to go about the installation. I've been using a live CD to access the file system up to this point...

> **lswest said:**
> check the permissions on the files you copied back over, it should be root for owner, root for group, read & write permissions for owner, and read for group and other.

Hmm good idea, I will try this when I get home later in the afternoon. Thanks!

---

### Post by puffyzacd on 2008-05-20
I looked at the permissions of the udev rules I copied over. Everything is as you suggested, so I guess we're back to square one.

Does anyone else have any ideas?

Thanks!

---

### Post by lswest on 2008-05-21
to install udev again when you're booted into the liveCD mount your filesystem ```
sudo mkdir /media/linux
sudo mount /dev/sda1 /media/linux
``` i assume the drive is sda and the partition is the first one, if this is not the case (check with sudo fdisk -l [that's a lower-case "L"]) then change it for your drive.  Then set that partition as the root filesystem with ```
sudo chroot /media/linux
``` and a ```
sudo apt-get install --reinstall udev
``` (as long as udev is the actual name of the package, i'm on a windows PC atm though, so i can't check) it should re-install it to your partition.

If this does actually install it to your partition, let me know ;) i think it would, but i've never tested it.

---

