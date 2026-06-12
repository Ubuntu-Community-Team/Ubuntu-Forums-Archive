---
title: "[SOLVED] 80GB IDE appears to have shrunk to 30GB"
date: 2007-07-30
forum: General Help
---

### Post by anim8 on 2007-07-30
Hi

I'm using the 64-Bit version of Feisty Fawn.

The drive in question is a Maxtor 6Y080L0 as a slave on the primary IDE channel.

I have created an ext3 partition using GParted, which displays the following information:

Partition: /dev/hdb1
Filesystem: ext3
Mountpoint: /media/hdb1
Size: 76.33GiB
Used: 1.37GiB
Unused: 74.95GiB

Problem is the properties of the drive in Nautilus indicate 30.1GB free space most of the time (it did temporarily increased to 71GB at one point). I have attempted to copy more than 30GB of data to be sure, though that fails as Nautilus insists there is only 30GB.

Also, the Lost+Found folder and my Virtual Machine folder appear and disappear in hdb1.

I've also used GParted on the live CD and Acronis Disk Director (both show the correct size).

This drive and the OS Hard Drive, another Maxtor 6Y080L0, (Win XP/Ubuntu dual-boot) were previously set up as cable select, though I had the same issue, hence I've reverted to Master/Slave. 

Any suggestions? I expect the drive to be OK as I was previously using it as an NTFS volume in Windows XP. 

Thanks

---

### Post by fjgaude on 2007-07-30
Try in a terminal the command:

sudo fdisk -l

enter your passwor

and see what you get.

Should show correctly the drive and its size.

If not, from your live CD, or with the drive unmounted, run fsck on the drive. Could be a bad segment or something like that.

frank

---

### Post by anim8 on 2007-07-30
Yes you're right.

fdisk shows exactly what it is: Disk /dev/hdb: 81.9 GB, 81964302336 bytes

Ran fsck and this came up clean, even with option -f.

Is there anything else you can suggest?

Thanks

---

### Post by fjgaude on 2007-07-30
Well, could it be the drive has stuff in the Trash? See if you can find where the stuff is, one way or the other.

Also, in Applications/Accessories/Disk Usage Analyzer menu you might find what is using the disk space.

frank

---

### Post by anim8 on 2007-07-30
Trash is empty.

Running the analyser on dev/hdb1 tells me there are no items and that it is currently 4.0KB in size.

What do you think the problem could be?

Thanks

---

### Post by fjgaude on 2007-07-30
The Analyzer is a GUI and should show all your drives and partitions, by file, if you click on the little down-ticks.

Look in /root and Trash and see what's there. And also .trash.

I can't suggest anything else. This is strange.

frank

---

### Post by anim8 on 2007-07-30
.Trash in home is empty.

I cannot see  .Trash in /root.

Thanks

---

### Post by fjgaude on 2007-07-30
It's a hidden file. Use <ctrl-h> to show hidden in File Manager. You are using Gnome?

While I'm thinking of it, did you ever delete while you were root a bunch of files? If you did, they are in the hidden file .Trash in /root.

frank

---

### Post by anim8 on 2007-07-30
Yep, I'm using Gnome and Nautilus.

The file browser is already set to show hidden files.

Using ls -la also does not show .Trash in /root.

Thanks

---

### Post by fjgaude on 2007-07-30
Remember, doing a sudo nautilus is not the same as nautilus. Are you sure you see hidden files when using a root nautilus?
When at the command line, your ls -la, you have cded to /root?

frank

---

### Post by anim8 on 2007-07-30
It's the same with sudo nautilus as well.

Here is my ls -la output:

user@linux:~$ cd /root
user@linux:/root$ ls -la
total 68
drwxr-xr-x 12 root root 4096 2007-07-30 23:46 .
drwxr-xr-x 22 root root 4096 2007-07-29 23:26 ..
-rw-r--r--  1 root root 2227 2006-12-20 15:50 .bashrc
drwx------  3 root root 4096 2007-07-30 09:57 .config
drwxr-xr-x  2 root root 4096 2007-07-30 23:46 Desktop
-rw-------  1 root root   16 2007-07-29 22:57 .esd_auth
drwx------  3 root root 4096 2007-07-30 23:46 .gconf
drwx------  2 root root 4096 2007-07-30 23:48 .gconfd
drwx------  4 root root 4096 2007-07-30 23:46 .gnome2
drwx------  2 root root 4096 2007-07-29 21:50 .gnome2_private
drwxr-xr-x  3 root root 4096 2007-07-30 23:46 .nautilus
-rw-r--r--  1 root root  141 2006-12-20 15:50 .profile
-rw-r--r--  1 root root 1323 2007-07-30 23:09 .recently-used.xbel
-rw-------  1 root root 1024 2007-07-29 23:51 .rnd
drwx------  3 root root 4096 2007-07-30 16:28 .synaptic
drwxr-xr-x  2 root root 4096 2007-07-29 23:52 .vmware
drwxr-xr-x  2 root root 4096 2007-04-15 13:07 .wapi
user@linux:/root$ 

Thanks

---

### Post by fjgaude on 2007-07-30
I'm out of suggestions... I'd reformat the drive and start over, but here again, I'm not you.

frank

---

### Post by anim8 on 2007-07-31
It's OK now, problem solved.

Restored fstab from backup.

Thanks for your help anyway!

---

### Post by fjgaude on 2007-07-31
Say, what was the problem that caused the issue, please? <smile>

frank

---

### Post by anim8 on 2007-07-31
I think there may have been some typo error in fstab that was preventing the drive from auto-mounting.

---

