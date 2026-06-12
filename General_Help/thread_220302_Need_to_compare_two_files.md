---
title: "Need to compare two files"
date: 2006-07-21
forum: General Help
---

### Post by joe343 on 2006-07-21
Hi,

I need to compare 2 big files using Ubuntu.  The 2 files are about 22gig each.

The diff command is not really good at handling big files so how could I do the compare ?

Any ideas on how to write a script that would do the job of splitting and comparing the slices ?

ps I'll be running the live cd for this.

Thanks.

---

### Post by fabiand on 2006-07-21
Hey,

if you just need to if they are different or not use a checksum like md5sum oder sha1sum.

Otherwise you can try to use diff in ocnjunction with hexdump/xxd

---

### Post by joe343 on 2006-07-21
Hi, thanks for the suggestion.  I could try to use checksum at first but if there a difference between the two files I will need to know those differences.

How reliable is the md5sum and sha1sum commands for big files ? If for example I there's "ab" somewhere at line number 41,443,908 in file #1 and there's "ba" at the exact same place in file #2, will the checksums be different for the two files ?

---

### Post by 3rdalbum on 2006-07-21
Mathematically, yes there should still be difference in the checksums of two big files where one has ba and the other has ab.

---

### Post by fabiand on 2006-07-21
hey,

actually there is currently some discussion about collisions when using md5 (that means, to modify a give text, so it produces the same checksum).
but in generall it is not very probable ... maybe that is the reason why md5sum is taken to verify iso-downloads.

anyway, if you want to very very sure that they ain't equal you can create both checksums md5 and sha ... if both of them equal both checksums of the second file, it is really really sure that they are identical.

---

