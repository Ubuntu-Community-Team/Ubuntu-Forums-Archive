---
title: "Unable to access secondary harddrive"
date: 2020-07-20
forum: General Help
---

### Post by ShadowCore on 2020-07-20
So, I have a 512GB SSD and one 4TB SATA drive for file storage. I want to format the 4TB /dev/sda2 and use it for downloads, so Transmission etc. can use it. When I run "Disks" and try to format, I get an error. How can I make the harddrive available to my user without using sudo?



[https://i.imgur.com/8KYKdEa.png](https://i.imgur.com/8KYKdEa.png)

---

### Post by zebra2 on 2020-07-20
The concept of formatting a hard drive without using sudo is foreign to me.  Open Gparted, choose your desired drive, choose format from the menu, choose the format type, enter your sudo password and you should have no problem formatting the drive. But you won't be able to format the drive without "admin" privilege.  Unless there is something else I'm not getting here. Incidentally, you won't be able to put an MBR or EXT format on that drive (more than 2gig). You will have to convert it to GPT format or something that supports 4gig.

---

### Post by ShadowCore on 2020-07-20
OK, so far so good. But I still can't seem to transfer files to the drives. Manually drag'n'drop with Tunar just fails, and trying to download to it with Transmission just gives "Error: Permission denied (/media/jonaz/drivenumbergoeshere/)

---

### Post by ActionParsnip on 2020-07-20
How did you mount the partition?

---

### Post by ShadowCore on 2020-07-20
I...didn't?! I installed the hardware, booted up Ubuntu and there it was.. :(

---

### Post by Morbius1 on 2020-07-20
Just a suggestion but the folks here would benefit from some usable facts.

Please post the output of the following commands:
```
sudo blkid -c /dev/null -o list
```
```
cat /etc/fstab
```

---

### Post by Dennis N on 2020-07-20
A newly-created partition's filesystem initially belongs to root.

You want to be the owner of that filesystem on sda2. If it is mounted at /mnt/data in /etc/fstab, for example, you execute in terminal:
```
sudo chown -R yourusername:yourusername /mnt/data
```
(substituting for 'yourusername', of course).

Then you will have full access to the partition.

---

### Post by ajgreeny on 2020-07-20
Do as **Dennis N** has suggested and you should be fine.

In future please do not add large images in the body of your posts as they can be a problem for users on phones or other small screens, and not all users have unlimited downloads, or the fast networks that we may generally be used to.

Please use the **attachment icon, a paperclip**, in the toolbar of the "Reply to Thread" window and point it to the image on your own hard drive.
On this forum we always prefer images as attachments rather than external image hosting sites as you used.

---

### Post by Morbius1 on 2020-07-20
Really would be great if we had some facts.

Dennis N's response would work as posted if the partition was formatted to say EXT4 and the mount point was as /mnt/data.

Won't do jack if the partition was formatted to NTFS. And if the mount point is at /media/jonaz/drivenumbergoeshere the only user that can get to "drivenumbergoeshere" is jonaz regardless of what its permissions happen to be.

Need to know how it was formatted, what the real mount point is, what crazy set of options the Disks utility used, and what users you expect to access it.

---

### Post by ShadowCore on 2020-07-21
jonaz@alien:~$ sudo blkid -c /dev/null -o list
[sudo] password for jonaz: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /snap/core18/1705 
/dev/loop1 squashfs         /snap/core18/1880 
/dev/loop2 squashfs         /snap/gnome-3-34-1804/24 
/dev/loop3 squashfs         /snap/gtk-common-themes/1506 
/dev/loop4 squashfs         /snap/snapd/8542 
/dev/loop5 squashfs         /snap/snap-store/433 
/dev/loop6 squashfs         /snap/snap-store/467 
/dev/loop7 squashfs         /snap/snapd/7264 
/dev/sda1  vfat             /boot/efi      53C2-17F3
/dev/sda2  ext4             (not mounted)  cd00bd94-44f3-4c55-9bf4-b187bd11253b
/dev/sdb1  vfat             (not mounted)  ABD6-4B76
/dev/sdb2  ext4             /              8a6acb20-8b5d-4ebf-896e-0302e1042da3
/dev/loop8 squashfs         /snap/gnome-3-34-1804/36

and

jonaz@alien:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=8a6acb20-8b5d-4ebf-896e-0302e1042da3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=53C2-17F3  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

---

### Post by ShadowCore on 2020-07-21
> **ajgreeny said:**
> Do as **Dennis N** has suggested and you should be fine.

In future please do not add large images in the body of your posts as they can be a problem for users on phones or other small screens, and not all users have unlimited downloads, or the fast networks that we may generally be used to.

Please use the **attachment icon, a paperclip**, in the toolbar of the "Reply to Thread" window and point it to the image on your own hard drive.
On this forum we always prefer images as attachments rather than external image hosting sites as you used.

My appologies :(

Dennis N's suggestion didn't work, going thru the other replies now.

---

### Post by Dennis N on 2020-07-21
Well, your output confirmed sda2 is ext4, so being some other type of filesystem is not it.
One possibility is that you did not create the mount point and mount the partition before executing the chown command.

---

### Post by ShadowCore on 2020-07-22
So, for someone who is new: When ever you have time, can you walk me thru it? I'm in no hurry, so just answer with the commands when you have time :)

---

### Post by Dennis N on 2020-07-25
> **ShadowCore said:**
> So, for someone who is new: When ever you have time, can you walk me thru it? I'm in no hurry, so just answer with the commands when you have time :)

1. Create the mount point (using /mnt/data as the mount point):
```
sudo mkdir /mnt/data
```
2. Change owner and group of this folder (xxx=your user name):
```
sudo chown -R xxx:xxx /mnt/data
```
3. Add a line to /etc/fstab to mount the sda2 partition at startup:
```
UUID=<put-uuid-of-sda2> /mnt/data ext4 defaults 0 2
```

reboot

Now you should have full access to that partition.

---

