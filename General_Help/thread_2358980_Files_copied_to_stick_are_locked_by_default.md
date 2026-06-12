---
title: "Files copied to stick are locked by default"
date: 2017-04-19
forum: General Help
---

### Post by SnuKies on 2017-04-19
Every time I copy something on my USB Stick, those files have a lock on their icon and cannot copy or do anything with them.
If I try to change the settings of "Others" to "Read and Write" I get the following error: "Sorry, could not change the permissions of "DISK_IMG": Error settings permissions: Read-Only file system"

How do I change it ?

---

### Post by TheFu on 2017-04-19
The file system on the USB stick determines whether and which permissions model is supported. Most USB sticks have either FAT32 or xfat file systems. These do not support Unix permissions.  The only way to control the permissions are with mount options - available only at mount time.

Basically, you have to mount the storage with the owner, group and permissions you want the files and directories to have.

There are multiple ways to mount storage.  The easiest to understand is to directly use the 'mount' command.
```
sudo mkdir -p /mnt/$LABEL3 ; sudo chown $UID:$GID  /mnt/$LABEL3 ;
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL3 /mnt/$LABEL3
```
Just change the variables to match your setup/needs/desires.  I'm using a disk label to mount to a specific location, but you can use UUID or the specific device (the device will change as the order of devices connected and removed changes).  I like the label method best.

Once you get this working, you might want to make it easier by using **autofs**. This is a way to plug in a flash drive, wait about 5 seconds, then just cd to the location where you expect the storage to be available. If it is available, you'll have access to the files and directories there.  I use autofs, since it is more convenient, but trying to access a storage area when the USB drive(s) aren't connected is an issue. Setting the timeout is very important or you could lock up the system. Google for "*ubuntu autofs*" to find a how-to.

Clear as mud?

---

### Post by Impavidus on 2017-04-19
If you never did anything to make it different, you should be able to simply plug in your usb drive and copy files to and from it. Which is clearly not the case on your computer.

Where do you get the lock icon? On the originals on the hard drive or on the copy on the usb drive? Can you still open the files for reading or are the files corrupted?

The Read-Only file system tells us it's not a permission problem. The entire file system (on the usb drive?) is read-only. This can mean a number of things:
- Maybe it was explicitly mounted read-only.
- It may be a file system type that's always read-only, like on an optical disc. But in that case you should never have been able to copy anything to it.
- The file system may be damaged and was mounted read-only to prevent further damage.
- The hardware may be broken.

---

### Post by coffeecat on 2017-04-19
> **SnuKies said:**
> Every time I copy something on my USB Stick, those files have a lock on their icon and cannot copy or do anything with them.

You don't say how the usb stick has been mounted, whether you simply plugged it in and it was automounted, or whether you used the mount command, or some other method. We need to see details of how it is mounted. The simplest way is to run this command in the terminal and post the output:

```
mount
```

A question: have you by chance installed the package "usbmount"? If you have, that will be the source of your problem. It is not designed for GUI systems, and it breaks automounting. So, if you have, uninstall it.

---

### Post by cmcanulty on 2017-04-19
Sometimes things are even simpler. I was confounded by this issue on a usb stick until I realized it had a physical lock switch, which is often the case on SD cards also.

---

