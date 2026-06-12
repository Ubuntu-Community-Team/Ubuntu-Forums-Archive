---
title: "Adding a partition to fstab"
date: 2006-12-10
forum: General Help
---

### Post by canadianwriterman on 2006-12-10
I've installed Kubuntu Edgy to dual boot alongside Ubuntu Edgy. Is there any way to add the Ubuntu partition to fstab in my Kubuntu install, so I can access the files on the Ubunbtu partition? Thanks for your help.

---

### Post by ciscosurfer on 2006-12-10
Yes.  First issue the following in a terminal and take note of the mount point of your Ubuntu partition```
sudo fdisk -l
```...that's a lower-case "L" not a "1".

From there, take the mount point for your Ubuntu partition and add it to your Kubuntu /etc/fstab file for automatic mounting in Kubuntu.

---

### Post by canadianwriterman on 2006-12-10
The output is:

/dev/sda3

Now, do I simply add /dev/sda3  /media/ubuntu

to fstab? When I added my Windows drive, I had to add:

/dev/sda2  /media/windows_ntfs  ntfs  nls=utf8,umask=0222  0  0

Thanks for your help.

---

### Post by ciscosurfer on 2006-12-10
> **canadianwriterman said:**
> The output is:

/dev/sda3

Now, do I simply add /dev/sda3  /media/ubuntu

to fstab? When I added my Windows drive, I had to add:

/dev/sda2  /media/windows_ntfs  ntfs  nls=utf8,umask=0222  0  0

Thanks for your help.The line should look something like this:

[B] /dev/sda3  /media/ubuntu   ext3    defaults,errors=remount-ro 0       1

[/B]just like your Ubuntu line in your fstab over there. :-)

---

### Post by canadianwriterman on 2006-12-10
Perfect! Thank you ciscoserver.

---

### Post by ciscosurfer on 2006-12-10
Ciscosurfer says, "You're quite welcome!" :-)

---

