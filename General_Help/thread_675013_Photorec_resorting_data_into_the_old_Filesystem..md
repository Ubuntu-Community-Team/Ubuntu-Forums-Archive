---
title: "Photorec: resorting data into the old Filesystem."
date: 2008-01-22
forum: General Help
---

### Post by DuKe2112 on 2008-01-22
I used GParted to move my NTFS partition to the left.
Unfortunately Gparted crashed in the process.

(Yes, I made a backup, but only one DvD of the most valuable data and I'd like to restore the rest if possible)

So now I have a HDD with Filesystem pointing to the !left! side of the HDD but most of the corresponding Data lying on the right side.

I can use PhotoRec to extract the data, but this way I get a huge load of single files sorted in a completely random matter. (Not to mention the countless rubbish txts.)

So, since I still have a complete filesystem. I'm searching now for a tool that could match the recovered files to an entry in the filesystem having the exact same size.

Would that be possible or does someone have a better idea?

Otherwise I would have to sort them manually. (easy for single files like videos, but difficult for those that have a folder structure eg a webside, or even a specific order like some picture galleries.)

Help would be appreciated.

.

---

### Post by Ocxic on 2008-01-22
try testdisk  from live cd,, it's in the repos and hopefully will help restore your original partitions on your drive, no guarantees tho.

---

### Post by az on 2008-01-22
And if testdisk doesn't work, then file carving is the only way to do it.  

The problem is if testdisk can't recover the partition, your filesystem is no longer there.  The contiguous files are there and can be found (carved), but since there is no metadata about each file, there is no way to sort them in the way they were sorted without a directory structure.

Foremost carves files and drops them into folders named by file type.  I find it a little better at carving than Photorec and it's easier to use the recovered files.

---

### Post by DuKe2112 on 2008-01-22
Yeah I had the oldest problem here (that one 50cm from the screen (; )

Figured out how to use Testdisk properly and it was able to find the old partition. 
I had Luck, that GParted crashed early enough to not overwrite its beginning.

Foremost might be better, but PhotoRec is easier to use, due to the menü.

Anyway, luckily I don't need either.

---

