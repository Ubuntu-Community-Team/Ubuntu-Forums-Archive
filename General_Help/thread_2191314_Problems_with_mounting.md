---
title: "Problems with mounting"
date: 2013-12-02
forum: General Help
---

### Post by sarahfoxnz on 2013-12-02
hello.

I am trying to connect to a USB drive - but it won't "mount".  - Do we need to mount things each time ?

I've googled on AUTO mounting & Think ive got a problem.


Ive tried FDISK, & then this command :-  sudo gedit /etc/fstab


RESULT :-


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=42a84c00-1291-4436-8ff0-55554182b9bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=99129bc1-b76b-4527-829d-0962f0d1fe80 none            swap    sw              0       0



How do i remount ? will it stop me from using the PC ? i DO NOT have an ubuntu disk to re-load it all

---

### Post by fantab on 2013-12-02
By default, when you connect a USB drive it is mounted automatically in Ubuntu. If your USB is NOT mounting then there could be some fault with it or the USB port it being plugged in.

So try another USB port, or check another USB drive to see if it is being mounted. 
Plugin the USB drive in question and post the output of the following command:
```
lsusb
```

EDIT: If there are any filesystem errors then too the USB drive will not mount... If you have access to a Windows PC, connect the drive to it and check, if there are any errors then Windows will correct it.

I am just stopping short of asking you to re-format the USB drive as reformatting will result in data loss on USb.

---

### Post by Bucky Ball on 2013-12-02
Can you see it in Gparted, even though it's not mounted, and if so what filesystem are you using? Do you know if the drive is NTFS or FAT filesystem? The permissions can sometimes be a bit tricky and might be what it is.

And as above, you are sure this was 'shut' in Windows if that was its last port of call? Right click>eject or safely remove from memory and not yanked out?

> **fantab said:**
> 
I am just stopping short of asking you to re-format the USB drive as reformatting will result in data loss on USb.

Don't do this, but do tell us what release you are using. No, it won't stop you from using the machine if the operating system is not on it and it is a storage drive. ;)

PS: Your fstab looks fine. That only concerns your boot and the USB drive shouldn't be there, but should be automounted when plugged in.

---

### Post by sarahfoxnz on 2013-12-02
i'll check GPARTED now. The drive is :-Seagate Wireless Plus  (hard drive with its in-built wifi).  its supposaed to be easy - But i spent 8 hours yesterday trying to install it.

i THINK ive got some files upladed to it. i also did have a USB connection - Saw it in Nautilus for a while, but the file-transfer timed out.  I uploaded files via WIFI.

i'll check that other programme now.  PS this seagate drive is brand-new

EDIT: cant see it on GPARTED

EDIT :- shall I post another thread ? - or here - I'm thinking of seeing if there is a NAUTILUS equivelant for IPAD2. (I can get/send files to/from my IPAD)

---

### Post by Bucky Ball on 2013-12-02
Oh, so this is like a network drive, supposed to connected wirelessly to your network? You can't connect to it via wifi or USB? Which exactly are you wanting to do?

If you're looking at wifi then you should make it part of the network via the router. Give it a static IP and set up the details for your router in there. Don't bother trying to connect wirelessly directly to the network drive. It is intended to visible on the network. You need to set up the details on the NAS drive manually I'd say. If you wanted to connect with it via one machine only you'd need to set the NAS with a static IP would be easiest then set up the details for you machine in the drive config and for the drive on your machine.

---

