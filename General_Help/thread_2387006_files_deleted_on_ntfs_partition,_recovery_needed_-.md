---
title: "files deleted on ntfs partition, recovery needed - please help"
date: 2018-03-13
forum: General Help
---

### Post by vlnikolic on 2018-03-13
hello everybody,


unfortunately using rm i've deleted accidentally files i need. this was the bad command (i've typed * in hurry, thus i've lost everything):

rm *.odt * -R

all the files was in directory stucture that is ntfs, and was mounted on xubuntu linux

i've tried recovery using ntfsundelete but in the given list there was no these files. 

is there any spell that i can use to recover my files?


thank you very much

p.s. i've tried with one windows software as well. i installed in in my windows partition (not the one that i've used for storing those files) and i have no success as well. the lists of files that i can restore from both of these softwares are similar - not even one of those files that i removed with rm is available for recovery...

---

### Post by wildmanne39 on 2018-03-13
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by hrsetrdr on 2018-03-13
You could try testdisk, it's billed to (amongst other things) be able to: "undelete files from FAT, exFAT, NTFS and ext2 filesystem."  

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

I've used [photorec]("https://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") to recover a variety of deleted file types.

Testdisk is in the repos, if you install testdisk you will also have photorec.

---

