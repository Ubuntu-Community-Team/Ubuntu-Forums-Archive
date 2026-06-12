---
title: "Re-installing Ubuntu does it destroy existing /home and /data"
date: 2022-04-30
forum: General Help
---

### Post by makem2 on 2022-04-30
I have a corrupt install of Ubuntu 21.10 which fails to boot from grub. The system was a dual boot with Windows 10 and I am able to access Windows10 from grub, but not Xubuntu.

When I made initial install I kept /, /home, /data, /games on separate partitions.

I have a live Ubuntu 22.04 USB and would like to know if installing this would destroy or keep the files in /home, /data, other partitions such as Windows 10 and /games partition.

I am thinking it may be possible first to back up the /home and /data partitions to one of the /games partitions which are accessible by both Windows and Ubuntu to safegard any loss.

---

### Post by yancek on 2022-04-30
Have you tried to repair boot?  You could try boot repair from the link below.  I would not first use it to try to repair but use the 2nd option on that page and select the Create BootInfo Summary option and post the link you get when it finishes here.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have separate partitions besides / (root), during the install make sure to select them in the installer to be used but do NOT format those partitions.  You should use the manual (Something Else) option.

---

### Post by makem2 on 2022-04-30
> **yancek said:**
> Have you tried to repair boot?  You could try boot repair from the link below.  I would not first use it to try to repair but use the 2nd option on that page and select the Create BootInfo Summary option and post the link you get when it finishes here.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have separate partitions besides / (root), during the install make sure to select them in the installer to be used but do NOT format those partitions.  You should use the manual (Something Else) option.

I was unaware of Bootrepair.

Thank you for taking the time to assist.

I was able to fsck the two partitions in question[URL="https://paste.ubuntu.com/p/nvsrQv858K/"]:
[/URL]
[Code]
xubuntu@xubuntu:~$ sudo umount /dev/nvme1n1p6
xubuntu@xubuntu:~$ sudo fsck -f /dev/nvme1n1p6
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/nvme1n1p6: 361377/4480448 files (2.4% non-contiguous), 11941932/17947392 blocks
xubuntu@xubuntu:~$ sudo fsck -f /dev/nvme1n1p5
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/nvme1n1p5: 325960/2321984 files (0.3% non-contiguous), 4430979/9277440 blocks
xubuntu@xubuntu:~$
[CODE]

I have created the Bootinfo summary:

[https://paste.ubuntu.com/p/nvsrQv858K/](https://paste.ubuntu.com/p/nvsrQv858K/)

Edit: I have read the output and will be able follow it if you agree. I am able to select the boot order in the UEFI firmware. 
[URL="https://paste.ubuntu.com/p/nvsrQv858K/"]
[/URL]

---

### Post by oldfred on 2022-04-30
With separate partitions, you should only reinstall using Something Else & select /home but DO NOT check the format box.
You should have good backups anyway.

But did Windows turn on fast start up? It does that with Windows updates.
And that sets hibernation flag which then prevents booting Windows from grub and mounting any NTFS partitions read write.
Since you have a NTFS partition in fstab, it may just need minutes to time out, and then it will be read only.

Better to use parameters in fstab for NTFS.
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
```
LABEL=ntfs-stuff     /media/ntfs-stuff    ntfs    nofail,noatime,windows_names,nosuid,uid=1000,gid=1000,fmask=0022,dmask=0022,async,big_writes  0   0
or these parameters:
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002


```
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by makem2 on 2022-04-30
> **oldfred said:**
> With separate partitions, you should only reinstall using Something Else & select /home but DO NOT check the format box.
You should have good backups anyway.

But did Windows turn on fast start up? It does that with Windows updates.
And that sets hibernation flag which then prevents booting Windows from grub and mounting any NTFS partitions read write.
Since you have a NTFS partition in fstab, it may just need minutes to time out, and then it will be read only.

Better to use parameters in fstab for NTFS.
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
```
LABEL=ntfs-stuff     /media/ntfs-stuff    ntfs    nofail,noatime,windows_names,nosuid,uid=1000,gid=1000,fmask=0022,dmask=0022,async,big_writes  0   0
or these parameters:
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002


```
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Windows fast start up is not turned on.

I don't have any problem starting Windows. The problem is starting Ubuntu and that is why I have been thinking of installing 22.04. The draw back there is the failure to detect windows. I know there is a fix for that but it concerns me.

---

### Post by makem2 on 2022-04-30
Duplicated post

---

### Post by makem2 on 2022-04-30
> **oldfred said:**
> With separate partitions, you should only reinstall using Something Else & select /home but DO NOT check the format box.
You should have good backups anyway.


Thank you for your input. I have decided to install 22.04 over the existing 21.10. However, I am at a loss having chosen 'something else' to choose where to put the boot loader.

When I get to the Installation type I find /dev/nvme0n1 is the default but I know 21.10 is present on /dev/nvme1n1p5.

Looking at the output from boot-repair it says:

No boot loader is installed in the MBR of /dev/nvme0n1.

No boot loader is installed in the MBR of /dev/nvme1n1

These are the only two drives.

---

### Post by oldfred on 2022-04-30
With UEFI, you do not install a boot loader to MBR. So that is correct.
You always specify a drive like /dev/sda or /dev/nvme0n1 for boot loader, but with UEFI and Ubuntu's Ubiquity installer, it really does not matter. It always installs to the ESP on whatever drive is seen as first drive.
Not sure with NVMe drives which drive installer would see as  first.
If you get a grub install error, you can just install the new grub with Boot-Repair & its advanced mode. Grub can easily be installed to any drive, its just a very old Ubiquity bug.

If issues, various work arounds posted in bug report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by makem2 on 2022-04-30
> **oldfred said:**
> With UEFI, you do not install a boot loader to MBR. So that is correct.
You always specify a drive like /dev/sda or /dev/nvme0n1 for boot loader, but with UEFI and Ubuntu's Ubiquity installer, it really does not matter. It always installs to the ESP on whatever drive is seen as first drive.
Not sure with NVMe drives which drive installer would see as  first.
If you get a grub install error, you can just install the new grub with Boot-Repair & its advanced mode. Grub can easily be installed to any drive, its just a very old Ubiquity bug.

If issues, various work arounds posted in bug report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Thank you for that. It seems the system has chosen /dev/nvme0n1 as the device for boot loader installation so I leave that.

However, when I highlight the partition /dev/nvme1n1p6 which I know is my home partition as you suggest, the install button is greyed out and I cannot proceed. It seems I must do something else to proceed.

Edit: I find that if I choose 'Change' I can choose the filetype, mount point and whether to format or not. I chose /dev/nvme1n1p5 as / and to be formatted. I chose /dev/nvme1n1p6 as /home and not to be formatted.

I left the following /dev/nvme1n1 partitions untouched:

p1, efi system
 p2, Microsoft Reserved partition
p3, ntfs recovery
p4, ntfs which I believe is data
p8 swap

Are you able to confirm this is correct before I confirm please?

---

### Post by oldfred on 2022-04-30
You can add additional mounts in fstab after install if desired.
Swap partition vs swap file has proponents on both sides.
Default now is swap file of 2GB. Many suggest swap partition is still somewhat better.
Unless you click on swap and say do not use, it will automatically choose that for swap partition.
And it will automatically use ESP on default drive. Only if default drive does not have ESP, will it error out on last part of install as it cannot install grub boot loader.

You only have to have / (root) to do an install. Everything else is optional.

---

### Post by makem2 on 2022-04-30
> **oldfred said:**
> You can add additional mounts in fstab after install if desired.
Swap partition vs swap file has proponents on both sides.
Default now is swap file of 2GB. Many suggest swap partition is still somewhat better.
Unless you click on swap and say do not use, it will automatically choose that for swap partition.
And it will automatically use ESP on default drive. Only if default drive does not have ESP, will it error out on last part of install as it cannot install grub boot loader.

You only have to have / (root) to do an install. Everything else is optional.

Thank you for your assistance. The fresh install completed perfectly without data loss.

I was a little disappointed as I thought the LTS version would have fixed the NVIDIA graphics problem I have suffered since the day I installed the card. Ubuntu fails to remember the dual screen settings.

But I am happy to be able to pursue that at a later date.

---

