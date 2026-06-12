---
title: "Which disk format?"
date: 2007-06-12
forum: General Help
---

### Post by Moonshine on 2007-06-12
Hi all,

I wish to share some folders with Samba to some Window XP clients. If I format the drive in ext3, will the Windows XP clients be able to read/write to it ok? Or should I choose a different format.

Thanks a bunch.

---

### Post by daschmidty on 2007-06-12
windows can read/write ext3 only with an add on driver like ifsee, but linux can write/read ntfs fairly well. Also both can access FAT32, but that is a dated and now somewhat limited FS, especially if you wan to use big files. I recommend one of the first two choices personally, leaning towards ext3 with an extra driver, as ext3 is a rock solid filesystem.

---

### Post by anaconda on 2007-06-12
> **Moonshine said:**
> Hi all,
I wish to share some folders with Samba to some Window XP clients. If I format the drive in ext3, will the Windows XP clients be able to read/write to it ok? Or should I choose a different format.
Thanks a bunch.

When you use samba it is the linux-host, which does all the writing to your ext3 disk, so windows can write to the samba share without any problems and without ext3 drivers. 
(the same goes both ways. if you share an ntfs drive in windows then linux can write to it even without ntfs/write drivers installed)

The answer is yes, and in linux use ext3!

---

### Post by Moonshine on 2007-06-12
Thanks guys....using ext3 and is working as intended :D

---

