---
title: "HW RAID to LinuxRAID - Harder than it would seem"
date: 2014-04-05
forum: General Help
---

### Post by litch84 on 2014-04-05
So I got sick of the HP SmartArray P410 not syncing properly and the SA P212 crashing and generally being a right pain to maintain and manage and have ultimately both died now (long story of complaints I won't go in to right now).

I've got near 20 disks, and 6 SATA ports on the mobo so I kinda needed another controller with a heap of ports.

Anyway, got my hands on a RocketRAID 2760A (24-port HBA that does JBOD) and that just about brings it up to the present tense.

So 2 x arrays of interest 1 with 4 x 2TB disks (That were in RAID5 on the P212 controller) and an 8 x 3TB (Previously on the P410), but for now we'll focus on the 4-disk array.

I know:
* The stripe size, 128K
* The RAID Level (5, obviously)
* There are 4 disks (/dev/sd[g-j]) - I'll refer to these as disk 1-4 respectively.
* Disk 1 is the first disk in the array. I know it's not the parity disk (at least for the first stripe) because it has the GPT partition on there, filesystem starts at 128s (64 KiB)
* Disk 4 has a garbled GPT partition header - very likely the parity disk for that first stripe

What I'm not sure about:
* Parity alignment after the first stripe, I'm guessing it's right aligned.

Now the issue I'm having is that to assemble this in MDADM I need to know the parity alignment, recently I've just been creating a loopback for each disk (so no data is actually written to the disks) and creating the array with different alignments to try and re-create it... BUT....No matter how I assemble it, the GPT partition disappears from the /dev/mdX device...

Example creation command:

mdadm --create --verbose --assume-clean -f -n4 -l5 -c128 -p right-symmetric /dev/md1 /dev/mapper/sd[ghij]

Can someone please explain:
a. Why this is the case? Does MDADM write it's superblock to the start of the disk?
b. Is there a way to manually tell it to assemble without writing anything to the disk to start with?

Thanks in advance.

---

### Post by litch84 on 2014-04-05
Found the answer to the issue - but not the solution.

Yes, MDADM does absorb the first few bytes of the disk (likely for the superblock):

Disk 1 filesystem id:
00010480  00 00 00 00 00 00 00 00  2f 6d 6e 74 2f 61 72 72  |......../mnt/arr|


/dev/md1 filesystem id:
00010080  00 00 00 00 00 00 00 00  2f 6d 6e 74 2f 61 72 72  |......../mnt/arr|
We lose 0x400 (1024) bytes - enough to kill the GPT table off.

Is there a way to make MDADM assemble that raid at sector 0 instead of offsetting the stripe 1024 byes?

---

### Post by frostschutz on 2014-04-05
Well, if you use -metadata=0.90, the metadata would be at the end of the disk. If you're already using device mapper you could just add a linear mapping to add some room for the metadata though. Although recent versions of mdadm also use a crazy data offset (128MiB).

I've outlined a method using device mapper directly here, so you can get RAID w/o metadata. It's in German but you seem to be familiar with commands already, so maybe it will give you some idea: [http://forum.ubuntuusers.de/topic/zugriff-auf-raid-5-verbund-wichtig/5/#post-6111707](http://forum.ubuntuusers.de/topic/zugriff-auf-raid-5-verbund-wichtig/5/#post-6111707)

It's possible to deduct the chunk size, drive order, layout etc. from the raw data, if it's unencrypted and you have one large enough easy to locate unfragmented file (like a several MB large JPEG from a digital camera).

---

