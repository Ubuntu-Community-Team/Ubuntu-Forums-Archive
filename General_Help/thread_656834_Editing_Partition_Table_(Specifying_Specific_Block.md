---
title: "Editing Partition Table (Specifying Specific Block Ranges)"
date: 2008-01-03
forum: General Help
---

### Post by i.wanna.corndog on 2008-01-03
I am attempting to repair my 60gb iPod. I tried using Windows, but it won't let me format a FAT32 partition larger than 32gb. The iPod drive has a read error around 8gb in, so I want to tell the partition to start around the 10gb mark and to use the rest of the drive.

Would there be a way to specifically edit the partition table without disrupting the firmware partition so that the second partition (the one containing music and files) begins at the 10gb mark? I can't seem to figure out how to do this with PartitionMagic.

Thanks in advance for any assistance you can offer!

---

### Post by n_i_c_k on 2008-01-03
The package 'parted' provides that ability, I think (I have not used it with an iPod).

---

