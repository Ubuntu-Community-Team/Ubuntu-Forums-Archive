---
title: "a question re. partitioning"
date: 2007-01-19
forum: General Help
---

### Post by Choad on 2007-01-19
i need to move a 70gig ext2 partition further down the hard disk so i can expand my ntfs partition.

how is this possible? gparted wont move it for me.

---

### Post by CroEragon on 2007-01-19
If there is swap or any other partition between two you want to merge, there is no way without ra partitioning.

---

### Post by Choad on 2007-01-19
hmmm looks like its time to start burning a lot of dvd's

laaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaame

:D

---

### Post by az on 2007-01-19
> **Choad said:**
> i need to move a 70gig ext2 partition further down the hard disk so i can expand my ntfs partition.

how is this possible? gparted wont move it for me.

How full is it?

---

### Post by Choad on 2007-01-19
9 gig free

and ubuntu has decided that it wont burn dual layer dvd's any more. and windows is distinctly lacking in quality burning software. i am stuck. i may actually have to use nero. i HATE nero!!!

---

### Post by Choad on 2007-01-19
what the ****!? 170mb for nero... talk about bloat...

---

### Post by az on 2007-01-19
> **Choad said:**
> 9 gig free


I doubt any partitioning software will be able to shrink that safely, no matter what they claim.  Parted (the GNU backend for partitioning) is paranoid and therefore very safe.  It will not do it.

---

### Post by Choad on 2007-01-20
> **azz said:**
> I doubt any partitioning software will be able to shrink that safely, no matter what they claim.  Parted (the GNU backend for partitioning) is paranoid and therefore very safe.  It will not do it.
it did shrink it for me tho ;) and it worked. i need it moved however. (ie more free space BEFORE it)

dont worry tho, im going the dvd route

---

