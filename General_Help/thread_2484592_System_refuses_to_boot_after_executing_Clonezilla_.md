---
title: "System refuses to boot after executing Clonezilla image back up"
date: 2023-03-03
forum: General Help
---

### Post by xanizen on 2023-03-03
I select grub boot loader, then Ubuntu prompts, 'Press Ctrl + C to cancel all filesystem checks in progress'

Then 2 minutes later, proceeds to 'emergency mode'.

The following messages display:

```
[  1.289707] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCIO.SATO.SPT5._GTF.DSSP], AE_NOT_FOUND (20220331/psargs-330)
[  1.289761] ACPI Error: Aborting method \_SB.PCIO.SATO.SPT5._GTF due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[  1.293432] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCIO.SATO.SPT5._GTF.DSSP], AE_NOT_FOUND (20220331/psargs-330)
[  1.293455] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCIO.SATO.SPT5._GTF due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
/dev/sda1: recovering journal
/dev/sda2: clean, 910261/90003008 files, 16990436/36000000 blocks
[  3.470724]
You are in emergency mode. After loggin in, type "journalctl -xb" to view system logs, "Systemctl reboot" to rebootm "systemctl default" or "exit"
to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):
  

```

The sda drive had the following partitions:
sda1: EFI boot partition about 300MB
sda2: Main ubuntu / root content, 144GB 
sda3: Swap, 8GB
sda4: ext4 parition set to 64GB in size, for standard storage.

I went ahead and connected the disk drive, that Clonezilla was supposed to back up the files to, and lsblk -f accurately shows it copied over the partitions.
**Edit**: I have a second computer system with Ubuntu.
```

sdb                                                                         
&#9500;&#9472;sdb1
&#9474;    vfat   FAT32       3104-52BB                                           
&#9500;&#9472;sdb2
&#9474;    ext4   1.0         4afb4978-7050-4415-a737-3e306b2c2dc2   65.6G    46% /media/kaign/4afb4978-7050-4415-a737-3e306b2c2dc2
&#9500;&#9472;sdb3
&#9474;    swap   1           45e50a0b-961a-4117-8de8-ad6c358a7477                
&#9492;&#9472;sdb4
     ext4   1.0         29066d10-b000-4f25-9b55-6520276cd1a3   55.7G     0% /media/kaign/29066d10-b000-4f25-9b55-6520276cd1a3

```

Unfortunately the guide I came across on how to use Clonezilla, didn't tell me how to just back up the sda2 (sdb2 in this case) partition, and only for the amount of space actually used.

When I booted the system, both drives were connected. I went ahead and disconnected the clone drive, and that did no good.

What would be the next course of action? Also I never set a 'root password' on the Ubuntu system, as entering sudo with the admin account was all that was necessary when configuring system files and performing installations.

---

### Post by oldfred on 2023-03-03
You are showing install on sdb, but messages are about sda?
Or is it same drive and plugging in flash drive changed drive order? Which often happens.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by xanizen on 2023-03-03
I had a second computer system with Ubuntu, to analyze the physical drives.

This is the output of boot repair analysis.
[https://paste.ubuntu.com/p/mfPjM9QMnD/](https://paste.ubuntu.com/p/mfPjM9QMnD/)


The drive that the files were backed up to is physically disconnected. Sdb, sdc, sdd, are veracrypt encrypted drives/partitions.
I have a 60 GB VM image of Windows 10 that's installed on a drive, not physically connected to the system, Virtual Box is installed in /, root path though.

**Edit**: The drive I backed up to, was defined in the fstab file, which is located in /etc/, and I  had to comment it out. Also I had to physically disconnect the drives SATA cable.
You can also perform lsblk and fdisk to delete the partition in 'emergency mode', /, will remain due to 'busy device message', but system will still boot.
Thanks to this post:
[https://unix.stackexchange.com/questions/696964/stuck-in-emergency-mode-after-cloning-my-system-with-clonezilla](https://unix.stackexchange.com/questions/696964/stuck-in-emergency-mode-after-cloning-my-system-with-clonezilla)

---

### Post by oldfred on 2023-03-03
I have seen this, but do not know about encrypted drives and if different:
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections
[https://wiki.archlinux.org/index.php/Autofs](https://wiki.archlinux.org/index.php/Autofs)
use noauto if mount issues
The current thinking is to modify your fstab declaration by adding two options to your list: noauto,x-systemd.automount:

You also are using UEFI boot, but have old grub boot loaders in gpt's protective MBR. 
Just be sure not to boot in BIOS/CSM/Legacy mode as it will just fail.

---

