---
title: "Installing Trusty tahr on Windows 7 caused problem"
date: 2014-10-17
forum: General Help
---

### Post by maxxi2 on 2014-10-17
I will explain my problem in points.

1.I had four drives C,D,E,F with Win 7 on C (250 GB partition ) and data in others.
2.I was in a mood to install xubuntu 14.04 in parallel with Win 7.In intallation it showed that i can install over windows without unmounting the drive.
3.I chose that option and after some processing an "error message" popped up.I dont remember the error.But when i pressed the the back button on GUI and started again to install,then Windows was gone.
4.At that moment I decided to install "Xubuntu" and do anything after wards.

Now I want to recover that data. I think that there was a problem caused in MBR or partition table thats why other partitions are in unreadable mode.I m messed up.

PLZ Help

---

### Post by andrea42 on 2014-10-17
How do I delete this post? I thought I was responding to your message.

---

### Post by ajgreeny on 2014-10-17
> **andrea42 said:**
> How do I delete this post? I thought I was responding to your message.
You can't delete it yourself.  Use the Report-post link at bottom left of the post and ask the mods to remove it.

---

### Post by yancek on 2014-10-17
Boot the Xubuntu installation medium to the Desktop, open a terminal and enter this command:  sudo fdisk -l(Lower Case Lettr L in the command) and post the output here which will tell us whether you still have any windows partitions.  If you don't remember the error message there's not much anyone here can do to help with it.

---

### Post by maxxi2 on 2014-10-20
> **yancek said:**
> Boot the Xubuntu installation medium to the Desktop, open a terminal and enter this command:  sudo fdisk -l(Lower Case Lettr L in the command) and post the output here which will tell us whether you still have any windows partitions.  If you don't remember the error message there's not much anyone here can do to help with it.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070b40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   83  Linux

Disk /dev/mapper/sda5_crypt: 999.9 GB, 999945142272 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953017856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/xubuntu--vg-root: 999.1 GB, 999095795712 bytes
255 heads, 63 sectors/track, 121466 cylinders, total 1951358976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/xubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/xubuntu--vg-swap_1: 801 MB, 801112064 bytes
255 heads, 63 sectors/track, 97 cylinders, total 1564672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/xubuntu--vg-swap_1 doesn't contain a valid partition table

---

### Post by maxxi2 on 2014-10-20
What is this sda2(extended in log)

---

### Post by oldfred on 2014-10-20
With MBR(msdos) partitioning you can only have 4 primary partitions. Since that was limiting, they converted one primary to be an extended partition and inside the extended partition you can have an unlimited number of logical partitions.
To avoid the confusion that Windows creates with "drives" which can be either a physical drive or a partition on one drive, Linux uses drive numbering like sda, sdb, sdc etc. And partitions then are the number after the drive or sda1, sda2, sdb1 etc.
You probably did not have 4 'drives; in Windows but 4 partitions.

And if you have /device/mapper/xubuntu--vg-swap_1 then you chose encrypted install. That will always show as an error as the encrypted file system cannot be read, as it should not. Only using your passphase can you unencrypt your data in your install, but temporary data that may go into swap will not be readable.

Full drive encryption always overwrites the entire drive (full drive) and encrypts everything. It also uses the advanced LVM partitioning.

While some tools may be able to recover some of you old data, since Ubuntu did not physically overwrite the entire drive, it will be a long involved process. Any data overwritten of course will be gone.  Best just to restore from you backups.

---

### Post by maxxi2 on 2014-10-23
Plz give me some info on recovery tools and commands.

---

### Post by Mark Phelps on 2014-10-23
> Now I want to recover that data. If that data was in Windows filesystem partitions, then read on ...

n my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

