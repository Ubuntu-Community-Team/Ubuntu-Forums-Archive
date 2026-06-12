---
title: "Grub boot failure"
date: 2020-10-03
forum: General Help
---

### Post by iezzat on 2020-10-03
Hello, I'm facing an issue after foolishly defragmenting the drives on windows (dual-boot config),the grub screen of death was the outcome. I tried to follow some guides but i feel that I'm no going anywhere as the linux partitions are not listed when using lfdisk.I've tried to use the boot-repair utility to no avail.Please find the log from the tool at the paste-bin listed below.I'd like to know if it's at all possible to fix ubuntu or should I resort to the less favourable option and re-install ubuntu.

[http://paste.ubuntu.com/p/jm2zbhH8yB/](http://paste.ubuntu.com/p/jm2zbhH8yB/)

---

### Post by oldfred on 2020-10-03
While you show a Ubuntu UEFI boot entry in UEFI, you show no Linux partitions.
But seem to have some unallocatted space at end of NVMe drive.

Boot-Repair also did a BIOS boot loader fix for your UEFI boot Windows, which it should not have done.
You now have Windows BIOS boot in gpt's protective MBR, that will not work. Its ok to leave it, as it will not otherwise interfere, but never try to boot in BIOS mode or you will get major errors.

Does testdisk show missing partition at end of NVMe drive?
Do you have any records/backups that show what partitioning was before? 

[https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by iezzat on 2020-10-03
Thanks a lot for you reply.Testdisk only showed external usb drives (I'm not sure of it should also detect windows partitions but it didn't show any of ubuntu's) and unfortunately I don't have a backup for what the partitioning was before.I've also forgot to mention that I'd expanded an ntfs partition with unallocated space (thinking it was harmless) using a 3rd party tool on windows.Is there anything I can do to at least retrieve the data on the ubuntu partitions before re-installing ubuntu?

---

### Post by CelticWarrior on 2020-10-03
> [COLOR=#000000]Is there anything I can do to at least retrieve the data on the ubuntu partitions before re-installing ubuntu?[/COLOR]
If even testdisk can't detect the partition(s) then no.

> [COLOR=#000000]I've also forgot to mention that I'd expanded an ntfs partition with unallocated space (thinking it was harmless) using a 3rd party tool on windows.[/COLOR]
Well, that explains it. Defrag is safe and couldn't be the cause.
Expanding a partition to what probably wasn't unallocated space but another partition that unnamed third-party tool wasn't aware of. Native Windows tools are enough for such operation and AFAIK they don't create this kind of problems. And in ANY case if you're about to manage partitions, no matter what tool or method, you MUST HAVE BACKUPS!

---

### Post by iezzat on 2020-10-03
I definetly should have had a backup but I was quite sure that the unallocated space was separate from the ubuntu partitions (20 gbs that I previously unallocated from the windows drive a while back and I noticed that there were further 50 gbs of unallocated space -before the doomed step- which I figured is windows' way of display ubuntu partitions since they matched in size to the total space I had allocated for ubuntu) and therefore I thought that wouldn't affect the ubuntu partitions.It was foolish of me obviously since I'm not quite sure how the 3rd party allocated the space and the extend volume in windows' disk management was greyed out but just for the sake of learning from my mistake,shouldn't windows recognize the ubuntu partitions and not classify them as unallocated space.

---

### Post by iezzat on 2020-10-03
I came across suggestion for tools that can guess partitions (namely gpart) and re-write them to the ssd drive.can you please take a look at the output log below and tell me if there's any chance I can recover the partitions.I've noticed that there are linux partitions guessed by the tool and their size matches up with the 5o gbs showing as unallocated space but I'm not sure of the feasibility of their restoration and if the tool have enough info to be able to restore them.is it wise to use sudo gpart -W /dev/nvme0n1 /dev/nvme0n1 to restore the partition table or is it not worth the risk? I really appreciate your help.

gpart output log for the command sudo gpart /dev/nvme0n1 :


Begin scan...
Possible partition(Windows NT/W2K FS), size(499mb), offset(1mb)
Possible partition(DOS FAT), size(99mb), offset(500mb)
Possible partition(Windows NT/W2K FS), size(277385mb), offset(615mb)
Possible partition(Windows NT/W2K FS), size(158385mb), offset(278000mb)
Possible partition(Linux ext2), size(14305mb), offset(436385mb)
Possible partition(Linux swap), size(30518mb), offset(450690mb)
Possible partition(Linux ext2), size(7178mb), offset(481208mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(DOS or Windows 95 with 32 bit FAT, LBA): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(Linux ext2 filesystem): invalid primary 
Partition(Linux swap or Solaris/x86): invalid primary 
Partition(Linux ext2 filesystem): invalid primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 499mb #s(1021952) s(2048-1023999)
   chs:  (1/0/1)-(499/63/32)d (1/0/1)-(499/63/32)r

Primary partition(2)
   type: 012(0x0C)(DOS or Windows 95 with 32 bit FAT, LBA)
   size: 99mb #s(202752) s(1024000-1226751)
   chs:  (500/0/1)-(598/63/32)d (500/0/1)-(598/63/32)r

Primary partition(3)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 277385mb #s(568084480) s(1259520-569343999)
   chs:  (615/0/1)-(1023/63/32)d (615/0/1)-(277999/63/32)r

Primary partition(4)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 158385mb #s(324372480) s(569344000-893716479)
   chs:  (1023/63/32)-(1023/63/32)d (278000/0/1)-(436384/63/32)r

---

### Post by CelticWarrior on 2020-10-03
> [COLOR=#000000]shouldn't windows recognize the ubuntu partitions and not classify them as unallocated space[/COLOR]
Windows does. The tool you used apparently doesn't. That alone is a huge red flag. That tool is the culprit.

---

### Post by oldfred on 2020-10-03
This would be very unusual partitioning, but is that what you did?
> Possible partition(Linux ext2), size(14305mb), offset(436385mb)
Possible partition(Linux swap), size(30518mb), offset(450690mb)
Possible partition(Linux ext2), size(7178mb), offset(481208mb)

Ubuntu now installs with a swap file, no swap partition. And swap file is 2GB and the normal suggestion for a swap partition (for primarily servers) is 4GB. Only if you want to hibernate which is not recommended would you have swap same size as RAM.

Probably ext4, but many tools just call it as in the extx family of partitions.

---

### Post by iezzat on 2020-10-04
yes,I believe  so. do you recommend writing the partition table?

---

### Post by oldfred on 2020-10-04
Do you have good backups?

I would also backup current partition table, so you can restore that if the change is not what you want or expect. Its just a small text file which you need to copy somewhere else.

backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/nvme0n1 > PT_nvme.txt
So you know sectors:
sudo parted /dev/sda unit s print

---

