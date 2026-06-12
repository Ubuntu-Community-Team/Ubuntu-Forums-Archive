---
title: "Corrupt OS Partition: &quot;Invalid Superblock CheckSum&quot; How to repair?"
date: 2019-03-15
forum: General Help
---

### Post by 777funk on 2019-03-15
I have two installs of Xubuntu (14.04 on one HDD and 18.04 on another) and an install of Win7 on a third HDD. I had some UEFI BIOS issues and couldn't reach Win7. I finally was able to get this back but somehow no have a problem with 18.04. The only changes I made (to my knowledge) were in the BIOS. I don't know how the 18.04 HDD is now corrupted, but I'd like to get it back if it's possible. Here are the error messages I'm seeing (crudely hand copied from a BIOS screen):
```

ACPI Error: DSSP Namespace lookup failure, AE_Not_Found 
fsck.ext4: Superblock checksum does not match superblock while trying to opene /dev/sdb2
The superblock coujld not be read or does not describe a valid ext2/ext3/ext4 file system (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

fsck exited with status code 8
[7.346186] EXT4-fs (sdb2): VFS: found ext4 filesystem with invalid superblock checksum 

mount: mounting /dev/sdb2 on /root failed: Bad message
:No such file or directory
Target filesyhstem doesn't have requested /sbin/init.
run-init": current directory on same filesystem as root: error0


try passing init= bootarg
Busybox v1.27.2 built-in shell (ash)

initramfs)_ <blinking cursor>
```

Is there any hope to get things working again?

---

### Post by oldfred on 2019-03-15
With multiple drives & multiple installs.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 777funk on 2019-03-15
Thanks for the tip. Here's what I end up with:

[http://paste.ubuntu.com/p/qM6qj92VJQ/](http://paste.ubuntu.com/p/qM6qj92VJQ/)

EDIT: That first link was dead.

As shown,  sdb is the drive in question.

---

### Post by 777funk on 2019-03-15
updated link. It looks like Windows has done the corruption... I have always dual booted and never had this before. Not sure why now.

Seems to be repaired after a bunch of manual running of this:
e2fsck -b 8193 <device>

---

### Post by oldfred on 2019-03-15
Do not run any autofix with Boot-Repair. That always tried to install grub to the MBR of every drive, and that is not what you want with multiple drives.
You want to keep the Windows BIOS boot loader in the MBR of sda, so you can directly boot Windows if needed.
Grub only boots working Windows, so when Windows needs repairs you may be able to directly boot with f8 to make repairs, but best to always have Windows repair flash drive.

You show gpt partitioning on sdb & sdc.
With sdc, you have grub in ESP for UEFI boot but also in MBR for BIOS boot. So it looks like you installed in UEFI mode & converted to BIOS boot mode or vice-versa. But have ESP - efi system partition mounted in /etc/fstab, so currently configured for UEFI boot on sdc drive.

You show UEFI Secure Boot on? That needs to be off to be able to boot Windows in BIOS/Legacy/CSM boot mode with new systems. Update to UEFI often resets UEFI to defaults. I keep a list and have 5 or 7 settings I have to redo with every UEFI update.

With newer gpt drives in BIOS boot mode, you need a bios_grub partition. It only needs to be 1 or 2MB, but must be within first 2TiB of a large drive. You can shrink any partition and add that partition. Since UEFI system, I would normally add both an ESP & bios_grub partition. I have done that for years with every new drive and even larger flash drives. Originally I used the bios_grub for BIOS boot, but had ESP, so I could move drive to a newer UEFI system. 

But you have Windows installed in the now very old BIOS/MBR configuration. And then Ubuntu has to boot in BIOS mode, to allow grub to boot a working Windows. Otherwise since UEFI, you can boot Windows from UEFI, by selecting sda drive, or boot Ubuntu in UEFI mode by selecting ubuntu entry. But UEFI Secure boot must be off to boot in BIOS mode. And grub can only boot other systems in same boot mode, as UEFI and BIOS are not compatible. But you can directly boot from UEFI if not in same boot mode. Some systems also need UEFI on/off or BIOS/CSM on/off settings.

Your sdc drive looks like it should boot in UEFI mode, or if adding bios_grub partition and using Boot-Repair's Advanced mode when booted in BIOS mode to fully uninstall & install the BIOS version of grub into sdc (only).
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
Your sdc is your 14.04 install and has a lot of old kernels. Best to house clean those.
       [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
New versions of Ubuntu only keep two versions, current or new & one older one that worked before.

Your sdb drive seems to have lots of issues.
Can you run a full fsck on each ext4 partition or do you get the same error messages?
       
 sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If still errors on partitions on sdb, what does  Smart Status show. You can use Disks and icon in upper right corner to check drives Smart status. It can run lots of tests but all I know is if it shows drive is good or bad.

---

### Post by 777funk on 2019-03-22
This problem was a rare set of circumstances and I was fortunate to get to the bottom of it. It turns out that Windows 7 was damaging 18.04 and I found out how. One more case of dual booting not playing nice. In this case in my Win 7 install, I had a program called Ext2Fsd which was designed to allow Windows to see Ext format drives (ext4 for example). Somehow, any time I booted into Windows, it'd corrupt the ext partitions that 18.04 resided upon. I removed Ext2Fsd from my list of programs in Windows 7 and now I can boot Windows without damaging my drive. I had to fix it with the above e2fsck trick one last time since booting Win7 to remove the offending program of course killed 18.04 one last time. But... I'm now happily typing from my 18.04 install after stumbling upon the solution (can't find the thread that pointed me in the right direction).

---

