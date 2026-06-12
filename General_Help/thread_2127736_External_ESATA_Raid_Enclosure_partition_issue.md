---
title: "External ESATA Raid Enclosure partition issue"
date: 2013-03-20
forum: General Help
---

### Post by Eagle1848 on 2013-03-20
First the setup:
I am a relative beginner in linux command line but have learned enough to install the packages I wanted on my HTPC such as XBMC. I am relatively experienced in computer tech though (working on my CCNP and been building PC's for over a decade) I am in a mixed OS environment (Win7 main PC and Ubuntu HTPC). The Raid enclosure is a 4 bay Startech with built in RAID. I have four 2 TB Samsung drives in a raid 5. In Windows 7 I partitioned and formatted using GPT and NTFS respectively. I then copied over a large quantity of data from my primary Raid 0 array in the main PC to be used on the HTPC. 

The problem is that the ESATA array works beautifully in windows through multiple power cycles of the system and drive array. However, when I try to put it on the HTPC Ubuntu reports the array as not having a partition and GParted says it is unallocated. The device itself does show up, however, Ubuntu does not see that partition that is on it. I verified it is there and functional by putting it back on my Windows PC. I scoured google and various forums and could not find an answer to this problem. 

As far as I can tell the problem stems from Gparted stating the array uses 512 byte sectors and Windows 7 stating it partitioned using 2048 byte sectors. GDisk did not find a GPT table on the array. Fdisk -l reports that /dev/sdb1 is there but blkid does not give me a uuid and does not see the partition at all. One further note Windows reads it as 5.5 TB total size. Ubuntu states it's 6TB. I don't know if that matters. I assume its because it isn't reading the sector size correctly. The way I understand it I shouldn't really try to manually force mount it through fstab until I can get a uuid, which I can't get without a readable partition. (will I can try to force mount it using /dev/sdb instead of uuid - but that isn't considered good practice anymore I guess? not to mention the possible data loss/corruption anyway from forcing a partition Ubuntu doesn't like)

Assuming I am correct and its that sector size problem is there a way to make Ubuntu read it? Either by using a program to edit the partition table, re-aligning the disk, or some other means. Or do I need to reformat it differently? Or am I missing something more...basic? I am trying to not lose the data as recopying it will take upwards of 8 hours minimum but if I have to, I have to. (for the time being I am keeping a perfect copy of the Raid 0 stored on the External Raid 5 and vice versa in case I do need to recopy it)

Any help is most appreciated.

Thank you

---

