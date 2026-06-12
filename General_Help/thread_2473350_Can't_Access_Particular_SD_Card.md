---
title: "Can't Access Particular SD Card"
date: 2022-04-01
forum: General Help
---

### Post by ts1971 on 2022-04-01
Hi,

I am running Ubuntu 20.04 on a Lenovo P70 and all of the sudden an SD card that I use very frequently became unreadable.  There are no errors that I see, but when I pop it into the drive nothing happens and if I open a term I don't see anything under /media.  All of my other SD cards still work fine.  I thought that maybe the card had just gone bad, but as it happens I have what I'm pretty sure is a bit for bit copy of the disk and it also isn't being read.  I tried inserting both files into a windows laptop and it complained about the format of both and wanted to reformat (obviously I didn't do that).  Shortly before this stopped working I had done a required Ubuntu upgrade; so that's possibly involved here.  I will also mention, in case it's relevant, that about the same time that this problem popped up Celluloid / MPV also stopped working.

I really don't want to lose this data; if anyone could point me in the right direction, I'd really appreciate it.

Thanks!

---

### Post by TheFu on 2022-04-03
SD cards fail. Usually there isn't any warning.  Sorry.
There are other things you can try, but if you use it all the time and it is over a year old, it is probably just worn out.

---

### Post by colin-i on 2022-04-03
Nothing under /media: not automounted. What **sudo fdisk -l** command is saying about the SD card?

---

