---
title: "Curious about  MBR"
date: 2007-07-20
forum: General Help
---

### Post by benanzo on 2007-07-20
I have a question about the data that is stored in the MBR on my disk and individual partitions.  I am not having any specific problems, I am just curious about some apparent discrepencies.

I have my disk split into four partitions:
```

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  10.2GB  10.2GB  primary  ext3              
 2      10.2GB  12.3GB  2097MB  primary  linux-swap        
 3      12.3GB  150GB   137GB   primary  ext3              
 4      150GB   160GB   10.5GB  primary  ext3         boot

```

Feisty / (root) installed on /dev/sda1, swap is /dev/sda2, /home is /dev/sda3 and I have Gutsy installed on /dev/sda4.  I have been playing around and investigating the MBR data on my disk recently and found something that perplexes me just a little.

When I use **dd** to copy out the MBR for the disk (/dev/sda) and then for each partition (/dev/sda1 sda2 etc) and then get info about the file using **file** I get this:

**/dev/sda**
```
mbr_sda: x86 boot sector; partition 1: ID=0x83, starthead 1, startsector 63, 19920537 sectors; partition 2: ID=0x82, starthead 254, startsector 19920600, 4096575 sectors; partition 3: ID=0x83, starthead 254, startsector 24017175, 268076655 sectors; partition 4: ID=0x83, active, starthead 254, startsector 292093830, 20482875 sectors, code offset 0x48
```
**/dev/sda1** (Feisty / (root)
```
mbr_sda1: x86 boot sector, code offset 0x48
```
**/dev/sda2** (swap)
```
mbr_sda2: data
```
**/dev/sda3** (Feisty /home)
```
mbr_sda3: data
```
**/dev/sda4** (Gutsy)
```
mbr_sda4: data
```

My question is regarding the lack of anything that indicates "active" or "bootable" on the Gutsy partition.  **parted** clearly shows that the **boot** flag is set, but the MBR just says **data**.  However, the **boot** flag is not set on **/dev/sda1** (Feisty) but the MBR indicates that it contains a boot sector.

Am I misunderstanding the way this works?  Like I said, I am experiencing no trouble booting into either Feisty or Gutsy with GRUB.  I am just curious so I can understand what is going on.

Thanks!

---

### Post by ddrichardson on 2007-07-20
The mbr says that partition 4 (Gutsy) is active.
```

mbr_sda: x86 boot sector; partition 1: ID=0x83, starthead 1, startsector 63, 19920537 sectors; partition 2: ID=0x82, starthead 254, startsector 19920600, 4096575 sectors; partition 3: ID=0x83, starthead 254, startsector 24017175, 268076655 sectors; [COLOR="Red"]partition 4: ID=0x83, active, starthead 254, startsector 292093830, 20482875 sectors, code offset 0x48[/COLOR]
```

Only sda has the MBR, the others are only partitions.

---

### Post by pistcivet on 2007-07-20
I just wanted to mention that you have 4 primary partitions, which is the limit.
You will not be able to add any more (if you would ever want to).

Better to make 1 primary, flag it as boot, and devote the rest of the space to 1 extended.
Then you can have as many logical partitions as you want in that extended partiton.
(up to 63? I think)

Also every hard disk has only 1 MBR.
Every partition has 1 boot sector.

Now what was the question again?  :lolflag:

---

