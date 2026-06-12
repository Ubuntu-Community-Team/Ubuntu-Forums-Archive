---
title: "mdadm raid drive missing after restart; parititions no longer show in fdisk/gparted"
date: 2024-02-24
forum: General Help
---

### Post by mike194 on 2024-02-24
Good morning!

I'm in the process of creating a RAID 1 array with two 2TB disks.  I was following [the instructions for mdadm on the kernel wiki]("https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Assembling_your_arrays")  and successfully started the RAID process.


```

sudo mdadm --create /dev/md/raid1 /dev/sda1 /dev/sdb1 --level=1 --raid-devices=2

```

I got carried away and restarted the computer before the sync completed.  When I rebooted, I saw that the partitions were gone.  ```
/etc/mdadm/mdadm.conf
``` didn't show any information about the RAID and gparted and fdisk both show the disk as physically fine but with no partitions.

I've gone down a rabbit hole of google searching and found [this]("https://unix.stackexchange.com/a/484532/429161"):
[INDENT]recreate the RAID with e.g. mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc /dev/sda

[/INDENT]
[FONT=arial]
[/FONT]I tried this command, noting the lack of partition numbers, and it still didn't work[FONT=arial].  I'm hoping that my data is still intact and can be recovered.  I'm tempted to recreate the partition table but not sure if that would even work.

Thanks!
[/FONT]

[INDENT][/INDENT]

---

### Post by TheFu on 2024-02-24
You can't magically ignore partitions if they've been created.

When it comes to everything here, just imagine someone is saying "prove it" for every statement you make. Then provide "proof" for every statement you make.
Prove there are or aren't partitions.
Prove there was an array.
Prove you ran any command you claim and show the command AND the output.

Always use forum code-tags when you post terminal output.

So ... "prove it."

BTW, RAID never replaces the need for backups.  Backups solve 1001 problems.  RAID solved 2.  Which do you think are more important?  BTW, backups also solve some RAID issues too, since RAID arrays with issues often need to be wiped and recreated from scratch, then the data put back from ..... the backups.  **You've been warned**.

---

### Post by mike194 on 2024-02-24
> **TheFu said:**
> You can't magically ignore partitions if they've been created.

I'm not ignoring partitions.  They simply aren't showing.

> **TheFu said:**
> Prove there are or aren't partitions.


```
mike@host:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000DM008-2FR1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

> **TheFu said:**
> Prove there was an array.
When I run testdisk, here's what shows:

```
Disk /dev/sda - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
>D Linux filesys. data         2046 3907028989 3907026944
 D Linux Raid                  2048 3906764807 3906762760 [starbuck:0]
 D Linux filesys. data         2048 3907028991 3907026944
```

> **TheFu said:**
> Prove you ran any command you claim and show the command AND the output.
I can't provide output from commands run after a reboot.  I don't capture all output from the terminal.  The best I can give you is my history:

```
   12  sudo mdadm --create /dev/md/viper /dev/sda1 /dev/sdb1 --level=1 --raid-devices=2
   13  sudo mdadm --assemble --scan
   14  cat /proc/mdstat
   15  sudo reboot
   16  cat /proc/mdstat
   17  cat /etc/mdadm/mdadm.conf 
   18  sudo mdadm --assemble --scan

```


> **TheFu said:**
> BTW, RAID never replaces the need for backups.  Backups solve 1001 problems.  RAID solved 2.  Which do you think are more important?  BTW, backups also solve some RAID issues too, since RAID arrays with issues often need to be wiped and recreated from scratch, then the data put back from ..... the backups.  **You've been warned**.

I feel like entering into the hows and whys of what I was trying to do my not be super relevant here.  I am fully, 100% aware that RAID doesn't solve the need for backups.  That said, I have found it woefully impractical to regularly back up terabytes of data using regular means.  My attempt was to build redundancy into my storage by adding a mirror.  mdadm seemed very straightforward and it looked like it was going to do what I expected.  After reboot, I was surprised that the mount disappeared.

I'm not ignorant of the issues here and I am fully prepared to rebuild the data, if necessary.  But would like to make that the absolute last option.

Thank you for the warning.  It's been heeded.

---

### Post by TheFu on 2024-02-25
After you assemble the RAID, did you put a volume manager+file system onto it or format it directly with a file system?  Without a file system, it can't really be used.

If partitions are disappearing, I'd strongly suspect the drive is failing.  I'd run a long SMART test and wait for that to complete. On HDDs, this can be many hours - 12+.  Then after it completes, get the SMART tool to output a report of the findings.

Testdisk is showing 3 possible partitions on the same storage locations - not 3 separate partitions.

BTW, the 2TB Seagate Disks had some of the worst reliability for any storage devices ever manufactured according to BackBlaze reliability reports.  I had 2 of them about a decade ago and both died right around the 1 yr warranty period.  I decided not to try an get warranty on the one that died BEFORE the 1 yr was ended. The other lasted 13 months.  I haven't bought another Seagate again.  Seagate had similar engineering issues with the 750G and larger disks in the early 2000s.  The failure rates were amazingly high and they denied, denied, denied any design issues.  Total lies.  In the 1990s, Seagate was my most used HDD vendor even with some overheating issues on their Barracuda disks.  Now, I won't touch them again. Ever. Life is to short to deal with liars.

---

