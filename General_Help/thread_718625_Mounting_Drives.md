---
title: "Mounting Drives"
date: 2008-03-08
forum: General Help
---

### Post by measekite on 2008-03-08
A few questions on mounting.

I have the following:

Desktop Computer
3 hard disks

Server Computer
2 hard disks

In the Desktop computer my boot drive is formatted in Linux.
The second drive is ntfs.
The third is an external usb

Both server drives are formatted with ntfs

Currently the file manager looks like this:

HomeFolder
Filesystem
dsk_vol2
usb_vol1
srv_vol1
srv_vol2

QUES 1

Can I mount all of the drives under my Home Folder so when I open my Home Folder all of the folders under the separate physical drives are shown?

QUES 2

If the answer to QUES 1 is NO then
Would it be yes if all of the drives were formatted with a Linux file system?

---

### Post by dabang on 2008-03-08
Mounting partitions does not depend on a filesystem (you may need special mount options though). Default mount point in Ubuntu is
```
/media/<partition>
```
I would leave it this way, but of course you could mount all partitions somewhere in your home directory. To do so, create some subdirectories within your home directory and than edit /etc/fstab accordingly.
Example:
```
cd
mkdir sda3
sudo gedit /etc/fstab
```
and change the mountpoint of sda3 to /home/<user_name>/sda3
You may then test this by doing a reboot and sda3 should be mounted in ~/sda3.
Hope I got you right?

---

### Post by hyperair on 2008-03-08
Quest 1 = YES

You just need to edit your /etc/fstab file. It isn't too hard. Or you could use... Storage Device Manager, found in the pysdm package.

---

### Post by measekite on 2008-03-08
> **dabang said:**
> Mounting partitions does not depend on a filesystem (you may need special mount options though). Default mount point in Ubuntu is
```
/media/<partition>
```I[COLOR=Red]** would leave it this way**[/COLOR], but of course you could mount all partitions somewhere in your home directory. To do so, create some subdirectories within your home directory and than edit /etc/fstab accordingly.
Example:
```
cd
mkdir sda3
sudo gedit /etc/fstab
```and change the mountpoint of sda3 to /home/<user_name>/sda3
You may then test this by doing a reboot and sda3 should be mounted in ~/sda3.
Hope I got you right?

**[COLOR=Red]Why would you leave it this way instead of choosing a mount point inside your home dir?[/COLOR]**

---

### Post by hyperair on 2008-03-08
Because /media is a partition meant for you to mount your drives, including thumb drives and memory cards. Your home directory is meant for you to store personal data, documents, settings and such. Not meant for mounting. However, you might have special reasons for mounting it in the home directory, like I used to, when I mounted my Music partition inside my home directory.

---

