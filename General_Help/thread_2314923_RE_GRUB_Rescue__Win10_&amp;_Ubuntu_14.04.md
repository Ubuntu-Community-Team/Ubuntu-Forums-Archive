---
title: "RE: GRUB Rescue : Win10 &amp; Ubuntu 14.04"
date: 2016-02-24
forum: General Help
---

### Post by Solo-Lux on 2016-02-24
[FONT=arial]Hello,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'm trying to multi boot MS Windows 10 & Ubuntu 14.04, but I keep ending up at the GRUB Rescue prompt.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I've found the Boot-Repair app and run it and I still get the GRUB Rescue prompt.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Here is the URL with the report that Boot-Repair created ...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/15175221/](http://paste.ubuntu.com/15175221/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Please can you help me ? 

Thanks, in advance ...

Solo-Lux[/FONT]

---

### Post by efflandt on 2016-02-25
I have noticed that many people with issues have partitions that are not in drive order (your sda3 partition is physically after your sda4 extended partition), but not sure if that really matters

I don't have a drive larger than 1 TB, but from what I have read, msdos partitions cannot be used on a drive larger than 2 TB (unless maybe the "logical" sector size is 4096 instead of 512?). So if your 3 TB drive has msdos partitions (mbr partition table) instead of gpt partitions, that might be your issue.

This is someone experimenting with trying to get around the 2 TB mbr drive limit with various operating systems including Linux:
[http://www.rodsbooks.com/gdisk/workarounds.html](http://www.rodsbooks.com/gdisk/workarounds.html)

Here is Window's point of view of the 2 TB mbr drive limit. It is a blog from or last updated 2010, although, there must be a miscalculation in whatever script/app handles comments, because some comments say 46 years ago. Note that at some point it mentions Windows "volumes", but last I knew that was proprietary and I do not know if Linux can access those:
[https://blogs.technet.microsoft.com/askcore/2010/02/18/understanding-the-2-tb-limit-in-windows-storage/](https://blogs.technet.microsoft.com/askcore/2010/02/18/understanding-the-2-tb-limit-in-windows-storage/)

---

### Post by oldfred on 2016-02-25
You have converted your 3TB drive to 2TB max. And with Windows in BIOS boot mode you cannot convert to gpt(GUID) and make it 3TB.
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.

So to use 3TB drive and boot Windows you need gpt partitioning and a UEFI system. And if system is UEFI then you would have to reinstall Windows in UEFI boot mode. Windows 7 can be UEFI, but you must convert to flash drive and move files around to make it UEFI bootable.

If system is BIOS, better to install Windows on smaller drive. Windows will read gpt for data, so you can have a large NTFS shared data partition.
Ubuntu can be installed in BIOS boot mode on gpt partitioned drive, but you need a tiny 1 or 2MB unformatted partition with the bios_grub flag, or if using gdisk code ef02. If drive may later be in newer UEFI system best to add the ESP - efi system partition at beginning of drive. Does not have to be large compared to size of drive or about 300 to 500MB, but better at beginning of drive. And difficult to add once drive has lots of data.

---

### Post by Solo-Lux on 2016-02-26
Hi,

Thanks for your time and information, however ...

I managed to get a little bit further, because I found this ...

[http://askubuntu.com/questions/438762/error-no-such-partition-entering-rescue-mode-grub-rescue](http://askubuntu.com/questions/438762/error-no-such-partition-entering-rescue-mode-grub-rescue)

Which basically says run these two commands ...

[COLOR=#000000][FONT=Arial]sudo apt-get install lilo[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo lilo -M /dev/sda mbr

By doing so this allows the computer to boot into Windows 10.

I know Ubuntu is on there, because it shows up when look at the disk partitions if I go to install Ubuntu, however for the moment I just can't boot into it.
I know it will run on that box, because Ubuntu runs perfectly from DVD ...

Thanks,
Solo-Lux.

[/FONT][/COLOR]

---

### Post by oldfred on 2016-02-26
What mode is drive in, in UEFI? It should be AHCI, not IDE nor RAID.
If you did not install Windows with AHCI then you will also need drivers for it.

Grub used to have an issue with very large drives. Supposed that was fixed several years ago.
But combination of very large drive and MBR on 3TB drive may be enough to create issues.
I normally suggest with very large drives, smaller system partition and large data partition(s) or with Ubuntu separate /home partition. I use large data partitions and my / (root) is normally about 25GB.

You could just use gparted to shrink / and reinstall grub with Boot-Repair. When we had issues with too large / partitions shrinking worked  about half the time.

---

### Post by Solo-Lux on 2016-02-26
Hi Oldfred,

Thanks for your reply ...

How do I determine what mode the drive is in ?

Thanks :-)

---

### Post by oldfred on 2016-02-26
You have to go into UEFI/BIOS and find tab with drive info. It should offer various drive options and one is drive mode. Typically with UEFI the default is AHCI, but the very old IDE mode is there for very old drives. Also RAID and maybe others, but you want AHCI.

Example is from my system, but every UEFI is different.

---

### Post by Solo-Lux on 2016-02-26
Ok thanks, I'll look into it :-)

---

