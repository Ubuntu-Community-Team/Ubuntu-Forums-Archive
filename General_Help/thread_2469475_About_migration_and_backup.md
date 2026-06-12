---
title: "About migration and backup"
date: 2021-11-30
forum: General Help
---

### Post by satimis on 2021-11-30
Hi all,

The 1TB NVMU PCIe 3.0x4 SSD is near full and it is solely running Ubuntu 20.04 and Oracle VirtualBox.  It needs to replace it with a 2TB NVMU PCIe 4.0x4 SSD.  

My ASUS motherboard has;
1 NVMU PCIe 3.0x4 socket
and
1 NVMU PCIe 4.0x4 socket.

Previously I have been considering Live migration and Live backup the old 1TB SSD to the 4TB WD HDD in the PC.  This 4TB HDD is solely for data storage without OS running nor partition created.

But Live migration running dd command line on Terminal is not reliable.  I must install a third party Live migration software.

Now I have another thought running a live USB installer to start the PC.  Then run dd command on Terminal migrating the Ubuntu 20.04 OS including VirtualBox from the old 1TB SSD to the new 2TB SSD.

Please advise whether this solution works?  Or there is a better solution.

Thanks in advance.

Regards

---

### Post by TheFu on 2021-11-30
Are you using LVM?  If so, you can leave the system running and use pvmove.
Or
you can create new mirror LVs, let the data sync and break the mirror.
I'm assuming that you want to leave the system up for some reason?  
Or
If that isn't the situation, you can use ddrescue to clone A-->B, and then change the UUIDs for partitions on A.  Then at the next boot, "B" will be used and all the old partition UUIDs will be retained.

There must be 20 other methods.  It is an ideal opportunity to validate your backup-restore processes. If they are NOT solid and tested, use this opportunity when there is next to zero risk.

---

### Post by satimis on 2021-11-30
> **TheFu said:**
> Are you using LVM?  If so, you can leave the system running and use pvmove.
Or
you can create new mirror LVs, let the data sync and break the mirror.
I'm assuming that you want to leave the system up for some reason?  
Or
If that isn't the situation, you can use ddrescue to clone A-->B, and then change the UUIDs for partitions on A.  Then at the next boot, "B" will be used and all the old partition UUIDs will be retained.

There must be 20 other methods.  It is an ideal opportunity to validate your backup-restore processes. If they are NOT solid and tested, use this opportunity when there is next to zero risk.
Thanks for your advice.

$ sudo fdisk -l | more ```

.....
Disk /dev/nvme0n1: 953.89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: INTEL SSDPEKNW010T8                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 271E9246-CC54-4368-8693-FDCC3EE8AB23

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux LVM
....
....
.....
```

The above shows the 1TB NVMe PCIe 3.0x4 SSD (/dev/nvme0n1)

Can I run pvmove to do the job and how ?

Is "LVM PvMove Method" on following document relevant to my case ?
How to migrate LVM to new storage
[https://www.casesup.com/category/knowledgebase/howtos/how-to-migrate-lvm-to-new-storage](https://www.casesup.com/category/knowledgebase/howtos/how-to-migrate-lvm-to-new-storage)

Thanks

Regards

---

### Post by oldfred on 2021-11-30
Do not know LVM.

But dd not recommended. It also copies all blank/unallocated space. And will convert your 4TB drive to 2TB (any other data on 4TB drive will be lost), and then you have to resize everything. Some have had issues with resize and needed vendor tools to have it work. And you have duplicate UUIDs & GUIDs. And two backup gpt partition tables, one at end of 2TB and one at end of 4TB, not sure what errors that will create.

If keeping both drives plugged in, you cannot reboot with duplicate UUIDs and GUIDS.
And you cannot easily copy one gpt partition as primary & backup partition tables & partition GUID all must match.

Or often better to do new install & test your restore procedure.

With two drives and Ubuntu's Ubiquity installer be careful of which drive, it installs the UEFI boot files. Ubiquity will default to first drive, no matter what you say during install. Be sure to partition in advance to have ESP on 4TB drive, best as first partition.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by HermanAB on 2021-11-30
I think you should read up on fsarchiver.

---

### Post by Tadaen_Sylvermane on 2021-11-30
Basically create the efi partition and lvm partition on the new 2tb drive. then add it to the volume group. ```
pvmove [COLOR=#000000][FONT=&quot]/dev/nvme0n1p2
``` which should move everything off that drive. It will take time but the system should remain fully usable. Don't forget that efi partition though because once the move is complete you will need to install grub to that new drive and update as needed. After this is done remove the 1tb drive from the vg then comment it out in fstab. Reboot and it should load the new drive. Then you can remove the other one whenever.[/FONT][/COLOR]

---

### Post by TheFu on 2021-11-30
> **satimis said:**
>  
Can I run pvmove to do the job and how ?

I think doing anything with LVM that doesn't include CAREFULLY reviewing the manpages and looking through REPUTABLE web tutorials would be a mistake. Don't just "wing it" and hope for the best.

I'd still strongly suggest using your backup/restore method for this. It is a great test and validation - and don't cheat by stealing data/settings from the old SSD. Only use the backups you'd have after a hurricane/tornado/earthquake flattened the server location.  The only way it would be better would be if 100% different hardware were used, since post-natural disaster, everything except your backups 500 miles away will be gone, gone, gone.  Much better to know that today and add all the issues to a list for resolution than not to know at all.  

I've said this many times. It took me 5 attempts to get my backups to contain everything I needed to perform a restore.  
The first restore attempt had a few chicken-egg issues. My backup storage was encrypted and I had carefully backed up the decryption key ... er ... inside the backups.  Obviously, that was a huge problem, since I needed access to the decryption key to access the  ... er ... decryption key. |-O. Not my proudest moment.   Over the decades, I've improved the backups, just a little each year. Adding more and more to be efficient for all sorts of issues, while also making the restore faster AND the amount of storage needed less.

Test your restore process, if it isn't 100% nail-down, perfect already. Please.

---

### Post by satimis on 2021-11-30
Hi all,

Lot of thanks for your advice and your time spent to help me.

I suppose the better solution for me is;
1. Retain the old 1TB NVMe PCIe 3.0x4 SSD
2. Add a new 2TB NVMe PCIe 4.0x4 SSD
3. Make the PC dual boot

On the new 2TB NVMe PCIe 4.0x4 SSD, I'll install Ubuntu 20.04 as host and KVM/QEMU as virtualizer.  All new work shall be performed on this new 2TB SSD.  Also I'll install Docker on the guest of KVM/QEMU.

This arrangement will save me lot of work and unforeseeable trouble.  I have tested running Docker, the Container, on VirtualBox.  I suppose it also works on KVM/QEMU

Comment would be welcome

Regards

---

### Post by TheFu on 2021-12-01
I hope you've found a solution. It isn't what we suggested as answers to the question.  We suggested using LVM methods (pvmove or mirroring) or testing your backup/restore processes (fsarchiver is an image-based backup, but it likes LVM snapshots). From the fsarchiver manpage:
```
       -A, --allow-rw-mounted
              Allow  to  save  a  filesystem which is mounted in read-write (live backup). By default fsarchiver
              fails with an error if the device is mounted in read-write mode which allows modifications  to  be
              done  on  the  filesystem  during  the  backup.  Modifications can drive to inconsistencies in the
              backup. Using LVM snapshots is the recommended way to make backups since it will  provide  consis&#8208;
              tency, but it is only available for filesystems which are on LVM logical volumes.
```
To be clear, I'm NOT suggesting using that switch, but to create an LVM snapshot of the LVs (sudo lvs) and use fsarchiver to create an optimized image of that snapshot)

I don't see any of those used in post #8.  If the goal has changed, that's fine.
Docker is full of issues. If you know how to deal with those, great.

---

