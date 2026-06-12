---
title: "Mounting USB drive as RO and unclean dismounts"
date: 2013-09-27
forum: General Help
---

### Post by timstanley1985 on 2013-09-27
Hi,

First time poster here so apologies if i have posted in the wrong section...


To cut a long story short, if i mount a USB drive as Read Only and then unplug it without unmounting it am i risking data loss or am i safe?

If it helps i currently have the disk formatted as exfat but am open to other cross platform partition types that allow >4GB files sizes (ntfs?? not aware of any others)

Thanks in advance.

Tim

---

### Post by Habitual on 2013-09-27
Tim:
> **timstanley1985 said:**
> if i mount a USB drive as Read Only and then unplug it without unmounting it am i risking data loss or am i safe?
*should be* okay here.

> **timstanley1985 said:**
> If it helps i currently have the disk formatted as exfat but am open to other cross platform partition types that allow >4GB files sizes (ntfs?? not aware of any others)

I have and use a 3T WD USB Drive for backups mounted as
```
/dev/sdb1     **[COLOR=#ff0000]/media/Keepers[/COLOR]** ntfs-3g    rw,uid=1000,gid=100,dmask=022,fmask=133 0 0
```
Edit: Sun Sep 29, 2013 - 11:05:39 AM EDT
Your uid and gid will be different.

This mimics the linux-file permissions for the NTFS formatted drive and is cross-platform friendly.
This is important as you may have to restore from this media without mucking about with File and Directory permissions and ownership issues.
Your /mount/point will be different.
I believe ntfs-3g is a component in most newer kernels these days. See [http://askubuntu.com/search?q=ntfs-3g](http://askubuntu.com/search?q=ntfs-3g) for some clarity about Ubuntu's implementation of it.

Obviously, if you choose ntfs-3g the drive and/or partition will have to be converted, if not converted then formatted ntfs.
gparted on a "LiveCD" should be able to do that.

Let us know...

Edit: Sat Sep 28, 2013 - 8:35:51 PM EDT
NOTE: You should use UUIDs for mounting partitions.
Please review and be comfortable with this [document.]("https://help.ubuntu.com/community/UsingUUID")

---

