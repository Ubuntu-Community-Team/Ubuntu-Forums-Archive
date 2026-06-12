---
title: "Formatted linux partition from windows"
date: 2013-09-05
forum: General Help
---

### Post by neutralise on 2013-09-05
My machine is partitioned into windows and linux, I accidentally did a 'quick format' from windows of my linux partition.

When I boot into linux I have access to 'grub rescue'.

Does anyone have advice on how to recover ideally the partition, but alternately my data?

---

### Post by Bashing-om on 2013-09-05
neutralise; Hey.

In situations like this, I have often seen that the utility "testdisk" is advised.
"testdisk" is available in the ubuntu repositories .. or one may download a .iso file and make a bootable disk.
For starters, try:
[http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

I have seen positive results posted using "testdisk" to recover in this situation.

[INDENT][INDENT][INDENT]press on
[/INDENT][/INDENT][/INDENT]

---

### Post by varunendra on 2013-09-06
+1 to testdisk.

With accidents like 'quick format', testdisk is a sure shot and perhaps the fastest tool to fix it. Should be a piece of cake for it to recover the partition with all the data on it.
Please follow : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You won't need the 'deeper search' (unless something more than 'quick format' happened).

---

