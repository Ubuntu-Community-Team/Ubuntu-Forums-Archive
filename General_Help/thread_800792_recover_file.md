---
title: "recover file"
date: 2008-05-20
forum: General Help
---

### Post by worldy on 2008-05-20
Is there any way to recover a file which i accidentaly deleted with the `rm`
command ? :confused:

---

### Post by pedro_orange on 2008-05-20
The manual for rm says:

" Note that if you use rm to remove a file, it  is  usually  possible to recover the contents of that file.  If you want more assurance that the contents are truly unrecoverable, consider using shred."

It's not easy though:

Have a look at: [http://adminlinux.blogspot.com/2006/09/recover-from-rm.html](http://adminlinux.blogspot.com/2006/09/recover-from-rm.html)

It may well be totally lost though, since you need to know alot about the file in the first place. On conventional UNIX systems rm was permanent if I remember correctly.

---

### Post by panayk on 2008-05-20
First off, I'd stop using anything that writes to the given partition. The data is not really lost until overwritten by another file. If the lost file was on the root or home partition, I'd boot off a live cd.

I had good luck recovering some photos lost in a similar fashion using a program called PhotoRec from the TestDisk suite. This is all part of the "testdisk" package in Ubuntu. For a list of supported file types (it's not just pictures): [http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

---

### Post by cdtech on 2008-05-20
Backups are soooo nice.....

---

