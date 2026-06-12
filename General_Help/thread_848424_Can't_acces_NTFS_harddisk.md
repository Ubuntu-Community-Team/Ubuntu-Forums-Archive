---
title: "Can't acces NTFS harddisk"
date: 2008-07-03
forum: General Help
---

### Post by dvdhaar on 2008-07-03
Hey :)

This week I decided to call it quits with windows. Having some experience with Ubuntu already I installed it, everything is going ok. Except for this problem.
I've got 2 harddrives, one which was formatted and Ubuntu was installed on. And another one for data. But I cant access my data drive because of this error:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdb1 /mnt/Local Disk/ -o force

Or add the option to the relevant row in the /etc/fstab file: 

/dev/sdb1 /media/Local Disk ntfs-3g force 0 0

I believe there is a messed up boot record on this drive, so I think that's why it can't access it. But I don't want to lose my data thats on it. I tried hooking it up to an external USB converter but I get the same error. I've tried force mounting it, but it doesn't work.

---

### Post by kuja on 2008-07-03
Yeah. this usually happens if the ntfs partition isn't cleanly unmounted before shutdown (like if there were a situation where you lost power suddenly or had to reach for the power button, that would do it, or if it were an external drive to begin with and it were suddenly unplugged during use, that would do it too). If force mounting hangs or fails to work, you might have to pop it in an external enclosure and find a machine with windows to plug it into to get it mountable in Linux again ... at least that's the conclusion that I came to when it happened to me once. 

I'd also recommend backing up and formatting the drive with a more friendly filesystem.

---

### Post by dave.mcdaniel on 2008-07-03
HI! Just to back up what kuja said. This happened to me a few weeks back. I placed the NTFS hard drive in a USB external hard enclosure and plugged in into a Winhoes machine and accessed the data. Safely removed the drive from the Winhoes machine and plugged it back into my Ubuntu machine. Data was and still is accessible.

---

### Post by dvdhaar on 2008-07-03
> **kuja said:**
> Yeah. this usually happens if the ntfs partition isn't cleanly unmounted before shutdown (like if there were a situation where you lost power suddenly or had to reach for the power button, that would do it, or if it were an external drive to begin with and it were suddenly unplugged during use, that would do it too). If force mounting hangs or fails to work, you might have to pop it in an external enclosure and find a machine with windows to plug it into to get it mountable in Linux again ... at least that's the conclusion that I came to when it happened to me once. 

I'd also recommend backing up and formatting the drive with a more friendly filesystem.

Wow, didn't know it was that easy.. It's working :) Thanks alot. 
Which filesystem would you recommend me to use?

---

### Post by caljohnsmith on 2008-07-03
Dvdhaar, if you ever run into that problem again of having a NTFS partition/HDD that is not shut down properly and won't mount in Ubuntu, just use this great program called "ntfsfix" in the repositories; it will fix the problems with the NTFS partition without having to boot up Windows and doing a proper shutdown. It's as simple as doing the following command:
```
sudo ntfsfix /dev/sda1   (or using whatever your NTFS drive/partition is)
```
I've found this can save alot of time and hassle. And about a "friendlier" filesystem, FAT32 is always a good choice, as both Windows and Linux have no problem with it. :)

EDIT: the package is actually called "ntfsprogs", and it contains the ntfsfix program. Thanks, kuja, for the correction.

---

### Post by VMC on 2008-07-03
> **caljohnsmith said:**
> Dvdhaar, if you ever run into that problem again of having a NTFS partition/HDD that is not shut down properly and won't mount in Ubuntu, just use this great program called "ntfsfix" in the repositories; it will fix the problems with the NTFS partition without having to boot up Windows and doing a proper shutdown. It's as simple as doing the following command:
```
sudo ntfsfix /dev/sda1   (or using whatever your NTFS drive/partition is)
```
I've found this can save alot of time and hassle. And about a "friendlier" filesystem, FAT32 is always a good choice, as both Windows and Linux have no problem with it. :)

LOL. Another way to keep Windows at bay! Good find.

---

### Post by kuja on 2008-07-05
> **dvdhaar said:**
> Wow, didn't know it was that easy.. It's working :) Thanks alot. 
Which filesystem would you recommend me to use?

Well, if windows compatibility is no longer a must, something like ext3 or xfs would work wonderfully.

---

### Post by kuja on 2008-07-05
> **caljohnsmith said:**
> Dvdhaar, if you ever run into that problem again of having a NTFS partition/HDD that is not shut down properly and won't mount in Ubuntu, just use this great program called "ntfsfix" in the repositories; it will fix the problems with the NTFS partition without having to boot up Windows and doing a proper shutdown. It's as simple as doing the following command:
```
sudo ntfsfix /dev/sda1   (or using whatever your NTFS drive/partition is)
```
I've found this can save alot of time and hassle. And about a "friendlier" filesystem, FAT32 is always a good choice, as both Windows and Linux have no problem with it. :)

It actually seems to be part of the "ntfsprogs" package, but thanks for the info.

---

### Post by caljohnsmith on 2008-07-05
> **kuja said:**
> It actually seems to be part of the "ntfsprogs" package, but thanks for the info.
You're right, my mistake. :)

---

