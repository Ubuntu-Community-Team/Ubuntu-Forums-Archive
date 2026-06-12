---
title: "Dualboot backup with Clonezilla --&gt; mismatched GPT MBR partition /dev/sda"
date: 2015-06-24
forum: General Help
---

### Post by newcomer83 on 2015-06-24
Hello,

I am trying to backup my dualboot system (Ubuntu / Windows 7) and I keep reading that Clonezilla Live is the best tool for that, but when I tried to use it I got the above-mentioned error about having two mismatched partition tables (GPT and MBR). I thought Clonezilla would just clone my drive "as is" (plus compression), no matter what was on there, but apparently it doesn't work in my case. When I looked around for solutions they were kinda like "delete one of the partitions, but be aware that you might lose all your data if you delete the wrong one, so better backup your data beforehand". So, ha ha ha. ¬_¬

To be exact, my PC previously had Windows XP Home + Ubuntu installed, with a subsequent upgrade from XP to Windows 7 Home Premium, followed by a reactivation of Grub. Also since I was new to Linux I created all of those partitions that were asked of me (Boot, Swap, etc. plus one FAT32 "data exchange drive" because I didn't realize Ubuntu could read and write all Windows drives effortlessly). So, yeah, all in all I have 7 partitions (4 Linux, 2 Windows, 1 exchange).

And last but not least: Since I followed the official advice on a size of the Boot partition (which is way too small), I had to use gParted multiple times to resize my partitions, moving very large parts of my drive's data around.

Nevertheless, my PC works, so I figured everything I did to it worked just fine.

So, I am assuming that GPT and MBR are the two partition tables from Ubuntu and Windows and I believe they are mismatched, because Windows ignores Linux or something. Therefore I don't really feel like deleting either of them, unless I'm wrong and both systems use the same partition table (or can be coaxed into doing that). Does anyone know what I could do? If CloneZilla Live can't handle this, feel free to tell me which software can do it, or how to do a byte-by-byte copy as a last resort.

Cheers
Alex

---

### Post by VMC on 2015-06-24
Read [Clonezilla Q&A # 124]("http://drbl.org/faq/fine-print.php?path=./2_System/116_unmatched_partition_table.faq#116_unmatched_partition_table.faq") regarding this issue.
If unsure what you have, type ```
sudo gdisk -l /dev/sda
``` from a terminal, but read the response warning about changing anything.
Edit: here's by 'mbr' only output:> Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

---

### Post by newcomer83 on 2015-06-24
I am getting the following report from gdisk:


> GPT fdisk (gdisk) version 0.8.8

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 

Does this mean my system has to be running on MBR? Can I choose "1" and somehow get rid of the damaged GPT? Or do I need GPT for something?

Cheers
Alex

---

### Post by VMC on 2015-06-24
Where's the rest of the message that shows the partitions info?

---

### Post by oldfred on 2015-06-24
Windows only boots from MBR partitioned drives with BIOS, and only from gpt partitioned drives with UEFI.
Ubuntu does not care, but better to follow Windows as to partitioning type. Although there are some advantages to gpt if only Linux as you can also boot Ubuntu in BIOS mode from gpt.

If drive really is MBR(msdos), you should not have gpt partition info on drive. We do that where users with pre-installed Windows 8 which is always UEFI/gpt, install Windows 7 which normally defaults to a BIOS install. Windows then does not fully convert to MBR, leaving a backup gpt partition table. But then you usually cannot install Linux as all the Linux tools see both MBR & gpt and only assume you want to erase one or the other.

If you just want to remove backup gpt partition table, fixparts is easier than gdisk, but you also can use gdisk. Fixparts if from the same developer as gdisk.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by newcomer83 on 2015-06-25
> **VMC said:**
> Where's the rest of the message that shows the partitions info?
There is nothing else there. But since it shows all the info your output showed as well, I don't understand what is missing.

> **oldfred said:**
> We do that where users with pre-installed Windows 8 which is  always UEFI/gpt, install Windows 7 which normally defaults to a BIOS  install.
I installed Windows 7 with a pre-installed Ubuntu. If Ubuntu uses GPT, this is the cause of my problems, right?

> **oldfred said:**
> Windows then does not fully convert to MBR, leaving a backup  gpt partition table. But then you usually cannot install Linux as all  the Linux tools see both MBR & gpt and only assume you want to erase  one or the other.
Ok, so Windows 7 destroyed my GPT, which means I am now using MBR and can't install any more Linux OSes until I delete GPT, right?

> **oldfred said:**
> If you just want to remove backup gpt partition table, fixparts is  easier than gdisk, but you also can use gdisk. Fixparts if from the same  developer as gdisk.
       FixParts is the easiest way to remove the stray GPT data. GPT  fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more  involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
I want to remove it if I'm absolutely certain that it's ok to do so. If Windows converted my GPT to MBR, then GPT was created by my Ubuntu, so I am kind of afraid I might lose all of my Ubuntu partitions if I delete GPT. Is this a valid concern? Or is my current OS definitely using my MBR table, because it's the only undamaged one?

Thanks for all your help and sorry for asking again and again. :-)

Cheers
Alex

---

### Post by VMC on 2015-06-25
> **newcomer83 said:**
> There is nothing else there. But since it shows all the info your output showed as well, I don't understand what is missing.

...
AlexThe partitions. Here's my full output:
```
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A5D9D6D1-4E7C-4689-A750-D5AFB009A46F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 12953 sectors (6.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       212723711   101.4 GiB   0700  Microsoft basic data
   2       212723712      1135349759   439.9 GiB   0700  Microsoft basic data
   5      1135351808      1139447807   2.0 GiB     8200  Linux swap
   6      1139449856      1346223293   98.6 GiB    8300  Linux filesystem
   7      1346226176      1490763285   68.9 GiB    8300  Linux filesystem
   8      1490765824      1953523711   220.7 GiB   8300  Linux filesystem

```

---

### Post by oldfred on 2015-06-25
You can convert MBR to gpt and vice-versa if partitions follow certain rules.
But I thought when Windows converted it would also erase Linux partitions, it does not correctly see Linux partitions so it does not include them when updating partition tables. Sometimes testdisk can restore missing partitions, but if part of conversion it gets more difficult.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

If you installed Windows in BIOS mode you cannot convert back to gpt without breaking Windows. 
Or you can install Windows 7 in UEFI boot mode if your system boots with UEFI.
Only Linux can boot in BIOS mode from gpt partitioned drives. 

Drives over 2.2TB must be gpt, but smaller drives can be either gpt or MBR.

---

### Post by newcomer83 on 2015-07-22
Sorry for the large delay, it has been a busy 3 weeks.

After I deleted GPT I was able to backup everything based on my MBR partition. I had Clonezilla check everything successfully, but I didn't test it by overwriting my current installation. I just assume that everything went fine.

So, thanks for all the help!

---

