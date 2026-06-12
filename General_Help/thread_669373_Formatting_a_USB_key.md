---
title: "Formatting a USB key"
date: 2008-01-16
forum: General Help
---

### Post by PaulFXH on 2008-01-16
OK, I know this has little, if anything, to do with Ubuntu but this is such a great forum that I'm more likely to get help here than elsewhere.
I have a 4GB USB key (Coskin) that I'm trying to partition/format with GParted.
Sounds very easy, but I'm having all sorts of problems.
It originally had just one FAT32 partition which I had intended to split into two EXT3 partitions (2.5 GB and 1.5 GB).
If I do the partitioning, it tells me all operations have been completed but then when I click OK and it goes to scan all devices, it comes back to tell me that the second EXT3 partition actually has an unknown FS.
If, I try again, I get the same thing.
If I try other FSs on the second partition (EXT2 or FAT32) I again get the same result -- an unknown FS.
OK, so I took out the second partition and increased the first one to 4 GB leaving it with EXT3. Again, all operations were completed sucessfully but when I click OK, this device (USB key) disappears from GParted.
Rebooting back to GParted and it shows up again, but the FS has become unknown.
Anybody know what's going wrong here?
Thanks 
Paul

---

