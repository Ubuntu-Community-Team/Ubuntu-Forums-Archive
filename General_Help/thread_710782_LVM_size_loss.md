---
title: "LVM size loss?"
date: 2008-02-28
forum: General Help
---

### Post by bluepowder7 on 2008-02-28
does anyone know how inefficient LVM is when combining hard drives?

i have 3 drives set up as one "group".  there's a 120G, a 250G, and a 750G.  even if the actual sizes are a bit smaller due to "marketing", i should have a total of just over 1TB.

now, the 750G was new and clean.  the 120G and 250G were full, but NTFS, so i set up the 750G as a solo drive in the LVM (which gave me 695GB or so - a bit small?), moved the contents of the 120G and 250G drives over, and then reformatted the 120G and 250G and added them to the LVM pool.  oh, i also moved over whatever stuff i had on my laptop's hard drive, roughly 90G worth of crud.

so, moving files off the 120G and 250G drives and then putting those drives back into the pool should cancel each other out, and mean that i still have around 750G of empty space, minus the 90G from the laptop.  so, i should expect 660G of available space, or a tiny bit less.

but - i only have 570G of space, and even if that 695G figure was real, moving only 90G over should put me at 605G, not 570G.  the whole thing is set up as an ext2 (or ext3, can't recall).  is it normal for that much space to get used up by marketing, the file system, and the LVM housekeeping stuff?  would somehow changing it all to JFS or some other file system help me regain the missing space?

---

### Post by articpenguin on 2008-02-28
yes try JFS it has a lot less overhead than ext2/ext3

---

### Post by bluepowder7 on 2008-02-28
am i really losing that much to filesystem overhead?  is there a table somewhere that shows the overheads for the various filesystems?  being purely a storage drive, i need max space with no fancy reserved spots.

---

### Post by pointone on 2008-02-29
[http://wiki.koshatul.com/Changing_Reserved_Space_on_EXT_Partitions](http://wiki.koshatul.com/Changing_Reserved_Space_on_EXT_Partitions)

[http://martin.ankerl.com/2008/01/12/get-more-space-out-of-your-ext3-partition/](http://martin.ankerl.com/2008/01/12/get-more-space-out-of-your-ext3-partition/)

---

### Post by bluepowder7 on 2008-02-29
damn, i just noticed that ext2 / ext3 have a volume size limit of 16TB.  that's not that far off from where i currently am.  looks like i'm gonna have to move away from ext2 / ext3 with the next drive i install and migrate it all to JFS or perhaps XFS.

i'll do that tweak for the existing drives, though!  thanks for the links.

---

