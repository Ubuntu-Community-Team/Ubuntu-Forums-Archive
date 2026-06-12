---
title: "How to make LiveCD detect and mount extend/LVM partition"
date: 2007-08-29
forum: General Help
---

### Post by satimis on 2007-08-29
Hi folks,


My HD has extend partition and LVM.  Is there any way to detect and mount them on running a LiveCD?


Made following test w/o result.

# fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       19457   156039345    5  Extended
/dev/sda5              32       19457   156039313+  8e  Linux LVM

```

sda1 is mounted automatically with its icon displayed on desktop.

# ls -al /media/sda1```

total 10410
drwxr-xr-x 4 root root    1024 Jul 24 10:21 .
drwxr-xr-x 6 root root    1024 Aug 29 06:14 ..
-rw-r--r-- 1 root root 1033449 Apr 15 02:28 System.map-2.6.20-15-generic
-rw-r--r-- 1 root root  407099 Apr 15 02:28 abi-2.6.20-15-generic
-rw-r--r-- 1 root root   75349 Apr 15 01:02 config-2.6.20-15-generic
drwxr-xr-x 2 root root    1024 Jul 24 10:22 grub
-rw-r--r-- 1 root root 7255399 Jul 24 10:21 initrd.img-2.6.20-15-generic
drwx------ 2 root root   12288 Jul 24 10:13 lost+found
-rw-r--r-- 1 root root   94600 Oct 20  2006 memtest86+.bin
-rw-r--r-- 1 root root 1726608 Apr 15 02:28 vmlinuz-2.6.20-15-generic

```


# ls /media/```

cdrom0  floppy0  sda1  sda5

```
sda5 seems mounted as well.


# ls -al /media/sda5```

total 2
drwxr-xr-x 2 root root 1024 Aug 29 06:14 .
drwxr-xr-x 6 root root 1024 Aug 29 06:14 ..

```
But nothing found on it.

Advice would be appreciated.  TIA


B.R.
satimis

---

### Post by MoLE on 2007-09-06
In the current Ubuntu release, I think on the Alternate CD has LVM support built in.

There is a launchpad blueprint for liveCD LVM support, but it hasn't been actioned as yet.

---

### Post by satimis on 2007-09-07
> **MoLE said:**
> In the current Ubuntu release, I think on the Alternate CD has LVM support built in.

There is a launchpad blueprint for liveCD LVM support, but it hasn't been actioned as yet.
Hi MoLE,

Tks for your advice.

I have my problem solved by running Knoppix LiveCD which has LVM tool running on it.

What is Altermate CD?  Ubuntu Live CD?\

B.R.
satimis

---

### Post by MoLE on 2007-09-10
The Alternate CD is the same release as the liveCD version, but has extra features including LVM at the cost of using a text mode menu-based install system.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom of the screen requesting the alternate CD.

HTH

MoLE

---

### Post by satimis on 2007-09-10
> **MoLE said:**
> The Alternate CD is the same release as the liveCD version, but has extra features including LVM at the cost of using a text mode menu-based install system.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom of the screen requesting the alternate CD.

Hi,

Tks for your advice.

What does it mean "....... This CD does not include the Live CD, instead it uses a text-based installer"?  Is it an installer running as a Live CD.  I can install Ubuntu from it if I need.

TIA


B.R.
satimis

---

### Post by MoLE on 2007-09-10
Thi s links explains it much better than I can: [https://help.ubuntu.com/community/CommonQuestions#head-593abe9d75618b67713ee23761b5cccf99befcbb](https://help.ubuntu.com/community/CommonQuestions#head-593abe9d75618b67713ee23761b5cccf99befcbb)

My understanding is that the Alternate CD provides expert support and flexibility in installing, but doesn't provide a desktop GUI to do the install in.

HTH

MoLE

---

### Post by satimis on 2007-09-10
> **MoLE said:**
> Thi s links explains it much better than I can: [https://help.ubuntu.com/community/CommonQuestions#head-593abe9d75618b67713ee23761b5cccf99befcbb](https://help.ubuntu.com/community/CommonQuestions#head-593abe9d75618b67713ee23761b5cccf99befcbb)

My understanding is that the Alternate CD provides expert support and flexibility in installing, but doesn't provide a desktop GUI to do the install in.

Hi MoLE,


Tks for your URL

If I understand it correctly;

Alternate CD is NOT an Ubuntu CD that runs directly off the Memory and the Disc, without installing anything to hard-disk.


I'm looking for an Ubuntu CD which can run directly off the memory and the CD withount installing it on the HD, similar to Knoppix.


B.R.
satimis

---

### Post by ergosys on 2007-09-22
You can do this with a regular Ubuntu live CD as long as you have internet access.   After booting, do the following in a terminal: 

sudo -i
aptitude install lvm2
modprobe dm_mod

Then you can execute normal lvm commands.

---

### Post by satimis on 2007-09-25
> **ergosys said:**
> You can do this with a regular Ubuntu live CD as long as you have internet access.   After booting, do the following in a terminal: 

sudo -i
aptitude install lvm2
modprobe dm_mod

Then you can execute normal lvm commands.
Tks for your advice.

What did you meant "a regular Ubuntu live CD"?  I only have installer CD here.  TIA


satimis

---

### Post by ergosys on 2007-09-26
By regular live CD, I meant the liveCD install disk as opposed to the "alternative" CD (which is recommended, maybe required, I don't know, for LVM installs).

---

