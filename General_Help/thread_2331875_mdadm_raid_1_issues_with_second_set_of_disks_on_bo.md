---
title: "mdadm raid 1 issues with second set of disks on boot"
date: 2016-07-26
forum: General Help
---

### Post by stray.light on 2016-07-26
Hello!  I have been working on a new build and have run into issues I have for the most part fixed myself but have run into one I'd like some help on.  I have built a system where I have 4 disks (2 SSDs, 2 HDDs) and have mdadm RAID 1 set.  This is a modern system so I have EFI running.  The SSDs are my boot disks and I have RAID 1 running on them successfully.  It is the HDDs which contain everything else I have issues.  Here are the mount points:

SSDs:
/boot/efi            sda1/sdb1
/boot       md0    sda2 /sdb2
/             md1    sda3/sdb3
HDDs:
swap       md2    sdd1
/tmp       md3    sdd2/sdc2
/src        md4    sdd3/sdc3
/var       md5     sdd4/sdc4
/home    md6    sdd5/sdc5

I followed this general guide: [https://guylabs.ch/2013/09/17/create-a-software-raid1-with-mdadm-on-an-active-ubuntu-13-04-hard-drive/](https://guylabs.ch/2013/09/17/create-a-software-raid1-with-mdadm-on-an-active-ubuntu-13-04-hard-drive/)
As I said, I got RAID 1 on the SSDs running and was booting fine.  I then used the same guide (more or less) to set up a degraded RAID 1 for the HDDs.  I got the arrays to synch except for md2 (swap) because even when booted off the Live CD I kept getting the "resource is busy" message every time I tried to add the second partition to the array (but this isn't what I'm looking for help on, though if there are ideas I'm open to them!  And no, there is no superblock on sdc1 which is what I'm trying to add).  When I rebooted after the HDDs synched, I got dumped to the emergency shell because of dev-disk-by "Failed to create volatile files and directories".

Is this because I have a broken fstab?  Or broken initramfs?  

I should have created the RAID before I ever installed but at the time I didn't know RAID wasn't an option in the install of Desktop (this is my first foray with Ubuntu, I have used RHEL/Fedora/CentOS in the past but those weren't working for me as I was also trying to do QEMU/KVM with VFIO for GPU passthrough which I got to work with Ubuntu).  Since I got the other hard bits working I didn't want to go back.  If anyone can point me in the right direction so I don't have to redo everything I would appreciate it.

---

