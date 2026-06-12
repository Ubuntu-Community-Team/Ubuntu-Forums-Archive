---
title: "Is it safe to fetch from ext3 with Windows?"
date: 2006-10-25
forum: General Help
---

### Post by noxxle on 2006-10-25
Do i risk corrupting data or partitions if i log into windows and copy data from ext3 to ntfs? if so, how can i do this? i have heard there are programs that allow for this, any recommendations??

---

### Post by bukwirm on 2006-10-25
I haven't had any problems so far - the only thing is Windows does not preserve permissions.

---

### Post by RRS on 2006-10-25
Had no problems myself. Used EXT2 IFS, you can get it [here]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm").

---

### Post by rejser on 2006-10-25
My windows always freaks out when having ext3 enabled, but on the other hand maybe it would either way (win don't like my hardware for some reason)

---

### Post by maddbaron on 2006-10-25
is there anyway for fat32 to read ext3?

---

### Post by crumja on 2006-10-25
[http://www.fs-driver.org/](http://www.fs-driver.org/)

This will give you read and write support to ext2 and ext3 drives on windows.

---

### Post by maddbaron on 2006-10-25
OMG THANK YOU!! It works perfectly I can see my files I can see my files!!!!! now I can burn what I need....thank you!

---

### Post by noxxle on 2006-10-25
just because none of you have had bad experiences with this program doesnt mean its "safe". i dont want to end up with a hard drive i need to reformat because i was copying ext2 files in windows to a ntfs filesystem. Any articles on this subject?

---

### Post by crumja on 2006-11-06
Well there's no way to be 100% certain with anything - bugs do appear. However, I can say from personal experience that the software is very conservative and hasn't failed yet on anything despite heavy usage. I run games stored on my ext3 drives from Windows and it hits the filesystem hard. It hasn't given yet.

---

