---
title: "Boot Repair"
date: 2024-02-04
forum: General Help
---

### Post by richardcar on 2024-02-04
I had Ubuntu 22.04.3 LTS running on a 480GB SATA SSD mounted at **sda1** and grub core at **sda2.**
I developed a boot issue and I tried to use Boot Repair but was completely confused.
I needed to keep working, so I reinstalled Ubuntu 22.04.3 LTS on a M.2 256GB SSD mounted at **nvme0n1p3.**
I copied all my documents from sda and was back in action.
That was about a month ago I. For various reasons I now need to get the original boot sector repaired.
Ideally I would like to have a dual boot option.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293389&stc=1[/IMG]
See paste bin link [https://paste.ubuntu.com/p/66ZqJ2bhs5/](https://paste.ubuntu.com/p/66ZqJ2bhs5/)
Any advice or help would be appreciated.

---

### Post by oldfred on 2024-02-04
Please rerun the Boot-Repair & post the link it gives to a pastebin site.
Many who are willing to help users will not download unknown files. 

If you run sudo update-grub does not your install offer to boot old install?

---

### Post by richardcar on 2024-02-05
Thanks,
I have added the paste URL to the post.
Result of sudo update-grub
[sudo] password for richard: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-15-generic
Found initrd image: /boot/initrd.img-6.5.0-15-generic
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Ubuntu 22.04.3 LTS (22.04) on /dev/sda1
Adding boot menu entry for UEFI Firmware Settings ...
done
richardcar

---

### Post by oldfred on 2024-02-05
your sda2 has grub's core.img. That is usually from a BIOS boot and in an unformatted partition with gpt.
Was this an ext4 partition before?

You also have issues with sde1, but that can only be resolved with Windows repair tools since NTFS.

---

### Post by richardcar on 2024-02-06
Thanks
You are Correct, 
GParted report on /dev/sda1
---------------
Partition       Name          File System     Mount Point
  /dev/sda2   BIOS-Boot  grub2core.img
  /dev/sda1                                       ext4  /media/richard/CT480G
---------------  

additional information
STARTUP OPTIONS
---------------
Ubuntu
 Advanced options for Ubuntu
 Ubuntu 22.04.3 LTS (22.04) (on /dev/sda1)
 Advanced options for Ubuntu 22.04.3 LTS (22.04) (on /dev/sda1)
 UEFI Firmware Settings
 -------------
 /sda BOOT SCREEN SHOT (this is just the bottom and keyboard entry not possible!)
 -------------
 mdadm: error opening /dev/md?*: No such file or directory
 mdadm: no devices listed in conf file were found,
 Gave up waiting for root file system device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the syatem wait long enough?)
 - Missing modules (cat /proc/modules: ls /dev)
ALERT!  UUID=**4ad3beea-9f8e-4407-8d23-f978e28e7dde** does not exist. Dropping to shell!

BusyBox v1.30. (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help' for a list of buily-in commands.

(initramfs)
--------------
sda FSTAB
--------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation

# CT480BX500SSD1 447.1GB SSD
UUID=**4ad3beea-9f8e-4407-8d23-f978e28e7dde** /               ext4    errors=remount-ro 0       1

Thanks richardcar

---

### Post by tea for one on 2024-02-07
> **richardcar said:**
> I needed to keep working, so I reinstalled Ubuntu 22.04.3 LTS on a M.2 256GB SSD mounted at **nvme0n1p3.**
I copied all my documents from sda and was back in action.
Line 137 - The boot-repair report indicates the you can boot in UEFI mode, which is perfect.
> **richardcar said:**
> For various reasons I now need to get the original boot sector repaired.
Ideally I would like to have a dual boot option.
Why do you still need the original OS on sda?
You already mentioned that you were "back in action"

Any reason not to install a fresh OS (UEFI + GPT) on sda?

---

### Post by richardcar on 2024-02-09
Hi tea for one
I don't **need** the OS on sda. But I am not in a hurry to scrap it either. I have only copied the /home Dir files into my new version. I wan to understand why I can't boot sda. When I am convinced I can not possibly fix the boot issue I will repurpose the drive.

[LIST]
[*]I don't understand message " ALERT!  UUID=**4ad3beea-9f8e-4407-8d23-f978e28e7dde** does not exist". When clearly this is the uuid of sda in /etc/fstab.
[*]Can you think of what the boot screen messaging is indicating.
[*]Can you expand on your suggestion to install a fresh OS (UEFI + GPT) on sda.
[*]Could I Delete/reformat sda2 and use Boot Repair to create new Boot partition??
[/LIST]

---

### Post by oldfred on 2024-02-09
Comment out the entry on line 299 from your fstab that trys to mount sda1 - [B]4ad3beea-9f8e-4407-8d23-f978e28e7dde. 

[/B]Youmay have corruption on that partition.
Have you tried fsck on that partition?#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by tea for one on 2024-02-10
> **richardcar said:**
> 
I don't **need** the OS on sda. But I am not in a hurry to scrap it either. I have only copied the /home Dir files into my new version. I wan to understand why I can't boot sda. When I am convinced I can not possibly fix the boot issue I will repurpose the drive.
Understood - an unquenched thirst for knowledge
> **richardcar said:**
> Can you expand on your suggestion to install a fresh OS (UEFI + GPT) on sda.
Happy to provide further details if/when the boot issue (sda above) proves stubborn

---

### Post by richardcar on 2024-02-12
oldfred
1. I commented out line "#UUID=4ad3beea-9f8e-4407-8d23-f978e28e7dde /               ext4    errors=remount-ro 0       1" from sda1/etc/fstab
2. I Logged on from a ubuntu usb stick, and ran fsck on sda1 and sdb1 as suggested. See result below.
====================================================================
sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
      591253 inodes used (2.03%, out of 29065216)
        6921 non-contiguous files (1.2%)
         554 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 551255/1521/5
    85735055 blocks used (73.74%, out of 116260352)
           0 bad blocks
          19 large files

      484630 regular files
       64677 directories
           8 character device files
           1 block device file
           0 fifos
         182 links
       41730 symbolic links (38257 fast symbolic links)
         198 sockets
------------
      591426 files
=========================================================
sudo e2fsck -C0 -p -f -v /dev/sdb1
                                                                               
         887 inodes used (0.01%, out of 15630336)
         255 non-contiguous files (28.7%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 869/10
     8659386 blocks used (13.85%, out of 62514432)
           0 bad blocks
           3 large files

         757 regular files
         121 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
         878 files
========================================================
sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      591253 inodes used (2.03%, out of 29065216)
        6921 non-contiguous files (1.2%)
         554 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 551255/1521/5
    85735055 blocks used (73.74%, out of 116260352)
           0 bad blocks
          19 large files

      484630 regular files
       64677 directories
           8 character device files
           1 block device file
           0 fifos
         182 links
       41730 symbolic links (38257 fast symbolic links)
         198 sockets
------------
      591426 files
=======================================================
sudo e2fsck -f -y -v /dev/sdb1
e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

         887 inodes used (0.01%, out of 15630336)
         255 non-contiguous files (28.7%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 869/10
     8659386 blocks used (13.85%, out of 62514432)
           0 bad blocks
           3 large files

         757 regular files
         121 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
         878 files
====================================================         
3. I logged on with Boot Repair usb utility, and got a Pre Boot Repair Summary [https://paste.ubuntu.com/p/2WT9dMmbFd/](https://paste.ubuntu.com/p/2WT9dMmbFd/)
4. I ran the Default Boot Repair, and got a Post Repair Boot Info [https://paste.ubuntu.com/p/P9zJQRTCVm/](https://paste.ubuntu.com/p/P9zJQRTCVm/)
5. I logged on and chose the sda1 option on the Boot menu. However The crash report is the same as before.


tea for one
This maybe a stupid question?
I am courious about sda2 when I compare it with nvme0n1p2 using lsblk.
It has neither UUID or mountpoint?
I previously asked "could I Delete/reformat sda2 and use Boot Repair to create a new boot partition?"

NAME          SIZE TYPE UUID                                 MOUNTPOINT
sda         447.1G disk                                      
&#9500;&#9472;sda1      443.5G part 4ad3beea-9f8e-4407-8d23-f978e28e7dde /media/richard/CT480G
&#9492;&#9472;sda2        3.6G part                                      
nvme0n1     238.5G disk                                      
&#9500;&#9472;nvme0n1p1     1M part                                      
&#9500;&#9472;nvme0n1p2   513M part 5198-E59E                            /boot/efi
&#9492;&#9472;nvme0n1p3   238G part 1bf0c288-ee6e-4da1-ba14-3128b66cfd2e /

---

### Post by tea for one on 2024-02-12
> **richardcar said:**
> I am courious about sda2 when I compare it with nvme0n1p2 using lsblk.
Info from pre-boot repair report post 10
Line 243 – sda2 			BIOS-Boot
Line 255 - nvme0n1p2 vfat    EFI System Partition

Your are comparing apples and pears
BIOS-Boot is for old-fashioned Legacy systems and EFI is for modern UEFI systems.

> **richardcar said:**
> I previously asked "could I Delete/reformat sda2 and use Boot Repair to create a new boot partition?"
Of course you can.
You own the device and you make the decisions.

But what would you choose?
Another ESP?
A new BIOS-Boot?
Something else in mind?

If you decide to try, please isolate/remove all other disks to avoid damage to your existing bootable OS.

---

### Post by yancek on 2024-02-12
> I developed a boot issue 

The above quote is from your initial post.  When you have problems like this, the first step to take is to begin taking notes of what happened and how it happened and any warning/error messages you saw.  Did you do that?  Because without that information, everyone here is left to guess.

What purpose do you think would be served by creating a boot partition?  The standard when using a gpt drive, which you have on both sda and the SSD, is to do an EFI install.  Your install on sda is a Legacy install with boot code in the MBR and a separate bios_boot partition, sda2.  The fact that it is sda2 rather than sda1 seems as it was an after thought or done after some problem.  Of course, we have no way of knowing this.

You have your Ubuntu installed on the SSD and have both a bios_boot partition (partition 1) and an EFI partition (partition 2).  There is no point in having both on an installed system.  You boot either in Legacy/CSM mode OR in EFI mode.

My experience is that a Linux system installed in EFI mode will boot another LInux system installed in Legacy/CSM mode as long as they are on different drives so there is something else wrong here.  A guess to a possible solution is to delete the bios_boot partitions after assuring that your BIOS is set to boot UEFI and Legacy/CSM boot is disabled.

What exactly do you get when you get when you try to boot from sda1?  Are you seeing the boot menu from the sda install, from the SSD install, by selecting it from the BIOS?

---

