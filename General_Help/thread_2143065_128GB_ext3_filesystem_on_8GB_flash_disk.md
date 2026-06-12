---
title: "128GB ext3 filesystem on 8GB flash disk"
date: 2013-05-07
forum: General Help
---

### Post by littlebonobo on 2013-05-07
Hello, all.

For some troubleshooting, I need to create an 128GB **ext3** filesystem on a 8GB flash drive. Of course, 120GB of that space needs to be marked as bad sectors, so only the 8GB that actually exist (those at the beginning of the partition) will be available for files.

I already tried this without much success. What I did:
[LIST]
[*]Partitioned the drive ‘normally’ (a single 8GB partition; actually an 8GB logical drive inside an 8GB extended partition);
[*]Used **Bless** to edit the partition tables to look as being 16 times larger that they actually are (128GB) and to zap (set to **FE FF FF**) the ‘CHS’ parts. At this stage the disk utility shows the expected 128GB partition/ logical drive, and a residual huge free space area that I don’t care about.
[*]Created a huge list of bad blocks. I *think* I got this right.
[*]Did a **mkfs.ext3 -l ***badblocksfile*** -b 4096 **etc. There are some warnings about superblocks being in defective areas of the disk, but I don’t think that is blocking because, as I understand it, those are backups and I don’t care that much about what happens if part of the drive becomes unreadable. Unfortunately, it seems the formatting still tries to write to blocks that I told it are bad and aborts at some point; the disk utility says ‘Unknown 128GB filesystem’.
[/LIST]

So, is this strange thing I want to obtain impossible? If not, what else to do? I almost did this for a **fat32** filesystem (works except I haven’t yet managed to mark the bad blocks), but I need **ext3**.

And a secondary question: what’s the exact format of the ‘bad blocks list’ expected by **mkfs.ext3**? I somehow figured out it’s a text file with one block number per line. Is it possible to specify block *ranges* instead? 120GB of bad blocks makes a really looong list of numbers… (especially since in the end I will need a 256GB filesystem with 240GB of bad sectors on a 16GB flash drive; for now I’m experimenting with a 8GB drive)

Note: I am using Ubuntu 12.04LTS.

---

