---
title: "How to recover an overwritten FAT16(?) memory stick's bootsector?"
date: 2008-03-09
forum: General Help
---

### Post by perixx on 2008-03-09
Hi people! 

Maybe seems to be a bit off-topic, but maybe there's still hope for me?


I've got trouble - nuked my memory stick's bootsector by mistakingly writing a NTFS bootsector to it, with 'Roadkil's Boot Builder' (Windows bootsector CHS tool). Unfortunately, it contains vital translation files ...argh!

Do you maybe have some advice on how to get it back? I'm convinced, that all the data's still in place and only the bootsector is wrong, because I've tried several recovery tools, of which 2 demo versions showed up with the complete root folder entries (but none could - or wanted - to retrieve data)...

After tinkering about with the (CHS) bootsector settings of the stick, I was able to get back (probably) the entire root folder content, but no usable data resulted from that action so far. The vendor wouldn't have (or want to provide) the appropriate data for this legacy stick's bootsector, but they told me all of their products would use LBA addressing. I thought, that basically LBA and CHS addressing would be possible to use in each other's place, if done correctly, so 'Boot Builder' would be able to restore the bootsector... 
but maybe you also know an LBA-based bootsector editor? Or can the 'dd' command help here?   


Here's what I've found out so far:

I'm fairly certain, that it's got to be FAT16; from what I know, FAT12 only is good for partitions as large as 32 MB's..? Anyway, when using Boot Builder, and playing around for prolonged time, I was able to get back the root directory of the stick!

But grieviously, no data can be gathered and only one folder is accessible - alas, it only contains 'crap'.

The following settings worked out the best:


> - FAT16 - though get's reported back as FAT12 to my astonishment, when setting:

- Bytes per Sector - 512 (seems to be the only working value)

- Sectors per Cluster - 32 (thought 2 would fit, but then I cannot reach the right size without altering Sec./Tr. and will not be able to access any folder)

- Rerved Sectors - 428 (seems the only working 'entry point' for a readable root dir, when working with the two FAT's, sized as follows. Can be adjusted according to the sectors needed by the FAT's, but will result in no accessible folder at all)

- Media Descriptor: HDD (258?)

- Sectors per Track - 32 (tried 16/32/63/64, it seems to be the only value resulting in where I'm at least able to access one folder, even if it contains only 'rubbish')

- Nr. of Heads - 16 (seems to make no difference, can be up to 255)

- Total Sectors - 125800 (obviously, a very 'tolerant' value - anything that produces sth. near 61MB seems to do)

- Serial Nr. - omitted that one

- Sectors per FAT - 32 (must comply to Sec. per Track?)

- Nr. of FAT's - 2

- Hidden Sectors - 47/57 (I've read, that hidden sectors names the number of sectors from the very first sector, to the actual beginning of the partition, but here it seems to make no difference...)

- Max. Root entries - 256/512 (seems to make no difference)

- Physical Nr. - omitted that

- Signature - omitted that 


Can you make something out of it, perhaps?

perixx

---

### Post by dcstar on 2008-03-10
> **perixx said:**
> Hi people! 

Maybe seems to be a bit off-topic, but maybe there's still hope for me?


I've got trouble - nuked my memory stick's bootsector by mistakingly writing a NTFS bootsector to it, with 'Roadkil's Boot Builder' (Windows bootsector CHS tool). Unfortunately, it contains vital translation files ...argh!
........

You have blown away your partition table, find a partition recovery tool and see if that can salvage anything.

---

### Post by perixx on 2008-03-10
Well, I've tried a dozen of recovery tools out there...
All I found out was, they won't find anything at all, won't suit for memory sticks, recover unusable trash or will show the lost stick's root folder (I got that far myself, remember?), but will demand registration and payment for non-proven real usability.

perixx

---

### Post by perixx on 2008-03-17
Well, I WAS able to get back some of my most vital data :) There was a trick about a certain demo version of a recovery program - also, I've read about a 'clone-format-restore' procedure that might work, but I'll try this the last... see my other thread here:

[http://ubuntuforums.org/showpost.php?p=4534172&postcount=7]("http://ubuntuforums.org/showpost.php?p=4534172&postcount=7")  

perixx

---

