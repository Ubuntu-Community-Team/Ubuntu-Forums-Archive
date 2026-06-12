---
title: "Repairing/recovering data from broken vista partition using ubuntu"
date: 2013-08-07
forum: General Help
---

### Post by nabla2 on 2013-08-07
Hi, I have Ubuntu 12.04 dual-booted with Vista home premium on my laptop and recently my vista partition kept crashing after a minute or so of the desktop loading. 

I managed to get into the vista desktop via safe mode at first, and checked the windows event log to find some recent "application event" errors (ID's: 10, 4609, and 6000), as well as some "system event" errors (such as ID's: 7001, 6008, 10005, 7026, 55, and more), which I had started to google, when safe mode started crashing as well. I manged to start safe mode command prompt, and ran "chkdsk", which spat out some details about the hard drive, which I can paste here if required. Then I tried "chkdsk /f /v" to which it spat out:

"file system is NTFS. Cannot lock current drive. In use by another process. Schedule for next restart? (y/n)"

After opting yes and restarting, chkdsk did not run, and it started trying to load windows again. Tried this multiple times with the same outcome. I also tried "sfc/scannow" which was recommended from googled, and it gave me:

"Beginning system scan. This process will take some time.
Beginning  verification phase of system scan.
Windows Resource Protection could not perform the requested operation."

After a few times of tring, I could no longer access the options to boot into one of the safe modes, and get a black screen after "Windows is loading files" with a windows cursor I can move. I tried booting from a Windows 7 installation disk (as its all I have avaialble), to access the repair console and attempt a repair, but the disk suffers the same problem. I also get the same problem tring to boot into the windows vista recover partition...unable to access the console, as it never loads that far.

Next I tried some free bootable partition managers, Gparted, and Mini Partition Wizard. I used the latter to rebuild my Master Booot Record (Since I was unable to access a windows command line to use bootrec.exe /rebuildbcd), but it didn't solve the problem...simply just removed GRUB loader, which I have now managed to restore, but with the same error as before when trying to load windows.

Gparted displays a red exclamation mark next to the vista partition, and clicking on it produces error messages about "Cluster accounting failed at: *[memory address]* missing cluster in $Bitmap" for a number of different disk addresses. I also tried running a disk check multiple times with Gparted and it crashes shortly after it begins each time, after leaving it overnight to wait even. It also gave a message about not being able to read the filesystem because "ntfsprogs or ntfs-3g" was needed.

Now I'm back in my Ubuntu partion, and have installed Gparted, ntfsprogs, and gpart, using "sudo apt-get", and I want to try and copy the files on the vista partition to an NTFS-formatted external hard drive by using ubuntu, so I can then reformat the vista partition and re-install windows. 

I'm still getting errors when clicking the partition within GParted installed on my Ubuntu partition about "input/output errors", "broken clusters" and "$Bitmaps", but I did some searching and tried the following to no avail:

```

root@matt-laptop:/home/matt# mkdir /mnt/ntfs
root@matt-laptop:/home/matt# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xad300cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    14706687     7352320   27  Hidden NTFS WinRE
/dev/sda2        14706688   328255911   156774612    7  HPFS/NTFS/exFAT
/dev/sda3       328256145   390716864    31230360    5  Extended
/dev/sda5       328256208   388050074    29896933+  83  Linux
/dev/sda6       388050138   390716864     1333363+  82  Linux swap / Solaris

root@matt-laptop:/home/matt# mount -t ntfs-3g /dev/sda2 /mnt/ntfs

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

The errors all sound pretty fatal, but if I'm running ubuntu fine on the same disk then I don't think it can possibl be a hardware error, and there must therefore be some solution to how I can solve this with software.

Apologies for the long-winded, convoluted post, but I tried to include evrything I've already tried, and would appreciate any more suggestions,

Cheers

---

### Post by gordintoronto on 2013-08-07
In Ubuntu 12.04, run Disk Utility. Click on your hard drive, and look at the SMART status on the right.

From Ubuntu, you should be able to view the folder tree and copy files to, for example, a flash drive or Ubuntu One or Dropbox.

Is there any chance that RAID is a factor?

---

### Post by nabla2 on 2013-08-08
Thanks for the reply. No I have no RAID configured as I only have a single 200GB drive (ATA TOSHIBA MK2546GSX_200). Thats exactly what I want to do, just recover as many of my files as possible to a USB hard drive.

I tried Disk Utility and it said the disk has 595 bad sectors, which are bad news, but even though its only a tiny percentage of the partition and full disk space, I reckon it must be this thats causing the problem and if they're not logical errors I could be looking at a hardware fault with the disk arm or something.

I tried mounting the drive using Disk Utility, but got an error saying the "Daemon is being Inhibited".

I also tried using the "rescue data" tool in Gparted ([http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-attempt-data-rescue](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-attempt-data-rescue)), which I left for a whole day and night, and kept checking back on it but it never got past the disk scan...it didn't crash because the loading bar was still moving back and forth, but that time seems unreasonable for a 200GB drive!

I'm gonna maybe try some other programs I've heard mentioned such as Photorec, TestDisk, Scalpel, and Foremost, else I don't think theres much else I could try, and probably have to accept the harddrive is broken.

---

### Post by gordintoronto on 2013-08-08
Your plan looks good!

---

