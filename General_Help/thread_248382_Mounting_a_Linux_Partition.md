---
title: "Mounting a Linux Partition"
date: 2006-09-01
forum: General Help
---

### Post by Goober on 2006-09-01
Hello fellow Ubuntians!

Ok, first let me outline my problem, and what I want to do.  My Main Harddrive recently decided to quit after 4 years of loyal service, rendering my computer unoperational.  That was my primary Harddrive, on which I had Grub, and Windows and such.  I have a second Harddrive, which is much newer. I want to keep some data that I want to from the secondary drive, and then wipe it, and re-install Drake and XP.  On the primary Harddrive, I had everything backed up, but not on the secondary.  I am currently using the Ubuntu 5.10 LiveCD, as I am unable to access the secondary CD.  On my secondary harddrive, I have 5.04 and 5.10 installed, in separate partitions, and an ntfs partition upon which I have a number of files that I want to keep.  

I can access the NTFS partition by mounting it with the LiveCD.  Therefore, I can mount it with the 5.10 installation too.  I am 99% sure that I have nothing I want to keep with the 5.04 and 5.10 partitions.  What I want to do it to mount that with the LiveCD, and ensure of that.  I am unsure of how to do this, however.  I know that I can show all my partitions with 

```
sudo fdisk -l
```

 and I can see the partitions.  I know they exist. I know the disk isn't corrupted. But what is the code to mount these partitions in a terminal?  I thought it was as follows:

```
sudo mount /dev/hdb1
```

But that doesn't work. Can anyone help me?

PS - I mounted the NTFS Partition thanks to this page: [http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)
PPS - I am going to recover the data from the NTFS by borrowing a friend's Portable Harddrive, and copying/pasting the information.

---

### Post by natrixgli on 2006-09-01
Hi,

Check /etc/fstab to see if they've been assigned mount points. If not, you have to create a place to mount them, i.e.: 

~$ mkdir /mnt/whatever1
~$ mkdir /mnt/whatever2
~$ sudo mount /dev/hdb1 /mnt/whatever1
~$ sudo mount /dev/hdb2 /mnt/whatever2

If this doesn't work, then post whatever error message you're getting.

-n8

---

### Post by Goober on 2006-09-01
Yay, that worked!  I have successfully loaded both of the Partitions, and am now saving the stuff from the one I want to keep to the one I don't want to keep.  

Thanks a lot for your help!

---

