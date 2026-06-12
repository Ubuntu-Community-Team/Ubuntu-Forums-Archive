---
title: "How to instal 3rd O/S"
date: 2008-05-23
forum: General Help
---

### Post by roundhay on 2008-05-23
I have Ubuntu 7.10 installed on a PC and Duel boot with XP. There are 4 HDD in the PC. 2 x 160GB HDD which are used for the operating systems, Ubuntu on one and XP on the other. The 2 x 500GB HDD are used for data storage.

I want to install Mythbuntu and have created a partition on the Ubuntu drive where this can be installed. The drive layout is below and I have attached the terminal info from fdisk -l. 

/dev/sda
/dev/sda1 ntfs

/dev/sdb
/dev/sdb ntfs

/dev/sdc
/dev/sdc1 ext3
/dev/sdc6 ext3
/dev/sdc5 swap

/dev/sdd
/dev/sdd1 ntfs

Can someone let me know what type of 'mount point' I should use when I install Mythbunbu? Should it be 'boot'???

The other info I need is how to amend the grub files so that I can boot mythbuntu from grub?

It looks like I have 2 boot partitions, on is the XP partition and one is the Ubuntu partition.

I would rather not get into reinstallation of Grub, I've had loads of problems with this in the past. I'm fairly sure you can add the mythbuntu o/s to grub by updating the menu.lst file in the /boot/grub folder of my existing Ubuntu installaion. This is the way I would like to go if possible?

---

### Post by RATM_Owns on 2008-05-23
Mount point = /
/ is the top of the filesystem.

---

### Post by ibuclaw on 2008-05-23
Yes, this is very possible...

The question I suppose you should ask, is "Will Mythbuntu let me choose whether or not I want to install a new GRUB?"

Even if it doesn't, you can still copy the menu.lst file from your Ubuntu partition into the Mythbuntu one, so it'll be like nothing changed.

[EDIT]
But to answer your questions:
**Can someone let me know what type of 'mount point' I should use when I install Mythbunbu? Should it be 'boot'???**
The Mountpoint for Mythbuntu will be just a plain forward-slash symbol; "/".
If you wish to include other filesystems with Mythbuntu, they will be under the "/media" Folder.

Also, when it comes to partitioning, just select "Manual".
Select the empty ext3 partition that you've created, click "Edit" and set the mountpoint to "/".

**The other info I need is how to amend the grub files so that I can boot mythbuntu from grub?**
Presuming Mythbuntu will install itself over your current GRUB, all you need to do is change the order of the lines in the "/boot/grub/menu.lst" file.

If you tell the installer NOT to install GRUB, then you can easily manually add a line later. (I'll go into detail when you need me to).

**It looks like I have 2 boot partitions, on is the XP partition and one is the Ubuntu partition.**
Yes, one may expect that. But do you have a third to install on?

Regards
Iain

---

### Post by roundhay on 2008-05-26
I have installed mythbuntu onto the partition I created. During the install I choose the advanced settings so that my esitsing grub files was not updated. When I log on I get my original grub with the options to choose the Ubuntu or XP OS but there is no option to choose mythbuntu.

How can I update the Grub file so that the mythbuntu istallion appears?

---

### Post by roundhay on 2008-05-27
Here are the outputs

********@HTPC:~$ df -h | grep /dev/sd
/dev/sdc1              71G  9.4G   58G  14% /
********@HTPC:~$ sudo fdisk -l | grep /dev/sd
[sudo] password for ********:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
/dev/sdc1   *           1        9313    74806641   83  Linux
/dev/sdc2            9314       19457    81481680    5  Extended
/dev/sdc5           18701       19457     6080571   82  Linux swap / Solaris
/dev/sdc6            9314       18700    75401014+  83  Linux
Disk /dev/sdd: 500.1 GB, 500107862016 bytes
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

---

### Post by roundhay on 2008-05-29
After sone help i have managed to install mythbuntu onto the partition I created and have updated my menu.lst file. I can now select the mythbuntu OS. The load screen appears but after a few minute the load screen disappears and I get the following message on a black screen:

[B]BusyBox v1.1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Enter 'help' for a list of built in commands

(initramfs)[/B]

Does anyine know why this is happening and what i can do to get the mythbunu OS to load correctly?

I have attached a copy of my menu.lst file

---

### Post by ibuclaw on 2008-05-29
Okay.
Seems like symlink to the initrd.img file is not there as I hoped.

OK, when in Ubuntu, mount the MythTV partition

```
sudo mount /dev/sdc6 /mnt
```
Then chroot to the partition
```
sudo chroot /mnt
```
You are now remotely inside the MythTV installation.
Change directory to the boot folder.
```
cd /boot
```
And list the files.
```
ls -1
```
Write down or copy the initrd.img and vmlinuz filenames
ie:
[PHP]
initrd.img-2.6.24-17-generic
vmlinuz-2.6.24-17-generic
[/PHP]
Then type in **exit** or close the window to leave.

Now re-open your menu.lst file and replace them with your current config in the menu.lst file.
To continue my example.
```

title		Mythbuntu 8.04
root		(hd1,5)
kernel		**/boot/vmlinuz-2.6.24-17-generic** root=UUID=b1d60638-5133-4b0d-9420-990de70a9735 ro quiet splash
initrd		**/boot/initrd.img-2.6.24-17-generic**
quiet

```

Iain

---

