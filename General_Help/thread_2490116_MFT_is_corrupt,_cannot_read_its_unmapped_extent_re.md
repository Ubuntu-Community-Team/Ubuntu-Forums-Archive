---
title: "MFT is corrupt, cannot read its unmapped extent record"
date: 2023-08-22
forum: General Help
---

### Post by mv-879 on 2023-08-22
hello everyone.

i broke my ntfs partition by using some windows partitioning tool trying to merge two partitions into one.

this is the situation after i messed things up: [https://i.imgur.com/W6mGMCf.png](https://i.imgur.com/W6mGMCf.png)

between what is now sdb2 and sdb3, there was small partition i will now call sdb2.5. i attempted to merge sdb2 and sdb2.5.

the sdb2.5 disappeared as a result of my action, but the merge was not correct. this is resulting error: [https://i.imgur.com/wmKJsBt.png](https://i.imgur.com/wmKJsBt.png)

so i obviously know it is not a hw problem.

i am now in the process of making copy of that partition before i attempt anything.

i have found some threads from people with similar problem (mft error and unable to mount the partition) but i wonder how much is my problem unique. 

someone successfully fixed his problem using "ntfsfix -b". somewhere else i read that there are actually two mft tables (one at the beginning and one at the end of the partition) and these various mft tool just replace the front one with the rear one. i wonder if that will work for me, since it is possible that at the end of the partition there is now rear mft from the former sdb2.5

i cannot use windows chkdsk since i don't have working windows rn, (what i broke was my windows system partition)

i don't know the precise partition sizes before.

other suggested tools i have found were ntfsclone and testdisk

if anyone has any suggestion, it would be highly appreciated!

thank you

---

### Post by mv-879 on 2023-08-22
so, i have a progress report:

deeper search of testdisk can find the sb2.5 partition and lists the sdb (system) partition at already merged size - [https://i.imgur.com/5DNEjWz.png](https://i.imgur.com/5DNEjWz.png)

the "list files" feature even correctly lists files for the sdb2.5 (not for sdb2 - [https://i.imgur.com/mmGYRm2.png](https://i.imgur.com/mmGYRm2.png))

so i need to find how to fix the size of the partitions (do i just leave them marked as deleted and use the add partitions to create new one of the correct size?) and then i will hopefully be able to repair the filesystem.

since it is past 4am here, it is a job for tomorrow.

i will be grateful for any tip i will potentially receive meanwhile.

---

### Post by mv-879 on 2023-08-23
so i just edited the partition size to match with the subsequent one and written the table and i was able to access the data on the disk. windows itself was still quite broken - i was able to boot into them, but the system was in unusable state, i honestly don't have idea why.

but i was able to backup data from documents and settings folder, which was what i was after.

---

