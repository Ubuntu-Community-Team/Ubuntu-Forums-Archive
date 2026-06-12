---
title: "Additional hard disk not showing"
date: 2021-09-22
forum: General Help
---

### Post by justaguyy on 2021-09-22
Hi Guys,
I purchased Dell Latitude last month which came with preinstalled windows 10. I have 2 hard disks in the laptop, one nvme 256GB  and one sata 1TB. So today I installed Ubuntu on the nvme drive, in which windows 10 was previously installed. After the installation, I don't see my secondary 1TB SATA hard disk, which was showing on windows 10.

Can you please help on how I can add my secondary hard disk?

---

### Post by &amp;KyT$0P# on 2021-09-22
Where is this disk not showing?

Have you checked in GParted (if you have it installed) and/or the output from running
```
lsblk -o +FSTYPE
```
in Terminal?

---

### Post by oldfred on 2021-09-22
What format is second drive?
If NTFS, did you leave Windows fast start up on? That sets hibernation flag.
If hibernation flag Linux NTFS driver will not mount the NTFS partition(s) to prevent damage.
Post this:
sudo parted -l

Best not to use NTFS with Linux as it will need chkdsk & defrag, which only can be run from Windows, not from Linux.
You can force mount manually as read/only and copy data to another drive. Then reformat to ext4.

---

### Post by justaguyy on 2021-09-23
Hi, Thanks for your time.

I can see my hard disk with lsblk (attached snapshot). But I still don't know how to mount it.

---

### Post by justaguyy on 2021-09-23
Hi, Thanks for your time.

I can see my hard disk with lsblk (snapshot link below). But I still don't know how to mount it.

[https://ibb.co/FVHT9P6](https://ibb.co/FVHT9P6)

---

### Post by justaguyy on 2021-09-23
Hi I have attached output of sudo parted -l. Still no clue what to do further.

[https://ibb.co/FVHT9P6](https://ibb.co/FVHT9P6)

---

### Post by Dennis N on 2021-09-23
Assuming the stuff on sda is of no importance and can be erased, I would just use the partition editor to make a new GPT partition table on sda, and then create new ext4 partition(s) for Linux use.

---

### Post by dragonfly41 on 2021-09-23
One point I note is that there is no Name attached to your ext4 partition.

---

### Post by justaguyy on 2021-09-23
> **Dennis N said:**
> Assuming the stuff on sda is of no importance and can be erased, I would just use the partition editor to make a new GPT partition table on sda, and then create new ext4 partition(s) for Linux use.

Hi, Thanks for your time.
There is no important data in my laptop.
I wanted 256GB Nvme for my OS and 1TB for my /home folder
Can you tell me how I can do that. If it means reinstalling, I can do that too.

---

### Post by justaguyy on 2021-09-23
> **dragonfly41 said:**
> One point I note is that there is no Name attached to your ext4 partition.

Hi, I don't know much about this, does no Name in my ext4 can cause any problem?

---

### Post by oldfred on 2021-09-23
You show one partition as bitlocker which is Windows only and other as NTFS which probably has fast start up/hibernation flag set on.
You could only open those two partitions if using Windows.

+1 on Dennis N's suggestion of a new gpt partition table. That in effect erases drive. 
Then you can partition it anyway you want.
In gparted, select device in top menu and change from default MBR(msdos) to gpt. It should warn you that it will erase drive. Make sure you have selected sda, not your NVMe drive.

I like to label every partition, particularly those I do not normally mount with fstab. Then the auto mount uses the label, not some long UUID where I do not know what partition it really is.
You can set labels with gparted, with disks (gnome disks) or command line.
With gpt there now are two labels, one used by gpt as partition and one by the filesystem which will be used if auto mounted by file browser.

---

### Post by Dennis N on 2021-09-23
> **justaguyy said:**
> Hi, Thanks for your time.
There is no important data in my laptop.
I wanted 256GB Nvme for my OS and 1TB for my /home folder
Can you tell me how I can do that. If it means reinstalling, I can do that too.

You have Ubuntu installed. To create a new partition table on sda, you boot Ubuntu and open the gparted application.
Then it will scan your disks. After that's done, select the sda drive in the drive selector in upper right.
 
Then in the gparted menu: Device > Create Partition Table.
Select GPT for type.
Without actually looking at it, I think you can then click on 'Apply' and it will do the job.
After that's done, make an ext4 partition for your use. In the menu: Patition > New.  You have to give some details on the format of the file system (should be ext4) and size of the partition - I would not use the entire disk at once. You might wish to add another one later on. 

You already have a home folder created during your install, and moving it now to the other disk is not trivial. You can ask here how to do that - start another thread. I've not done it, so won't give advice.

There is always the option of reinstalling and setting up the home folder on sda during installation.  


On Names for partitions, they don't require one. Also, only partitions on GPT disks can be given names.

---

### Post by TheFu on 2021-09-23
How to mount partitions with native Linux file systems: [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
This uses a "LABEL" method. There are others (device name, UUID, etc), but humans can understand and use the LABEL easiest.
That post also says which file system type to be used for different purposes, which users coming from MS-Windows usually aren't ready to handle in a smart way.

There is also an *Ubuntu fstab How-To* that google can find easily. It deals with more complex situations which may or may not be helpful. Only you can decide.

---

