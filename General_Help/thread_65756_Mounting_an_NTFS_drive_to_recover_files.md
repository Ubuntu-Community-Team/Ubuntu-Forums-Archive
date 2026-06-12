---
title: "Mounting an NTFS drive to recover files"
date: 2005-09-14
forum: General Help
---

### Post by Orunitia on 2005-09-14
I'm trying to mount an NTFS drive from a live cd to recover some files. I plan to copy the files over to a FAT32 drive. Is it possible to do this? If it is, could you tell me exactly how.

---

### Post by mlomker on 2005-09-14
[QUOTE=Orunitia]I'm trying to mount an NTFS drive from a live cd to recover some files. I plan to copy the files over to a FAT32 drive. Is it possible to do this? If it is, could you tell me exactly how.[/QUOTE]

I probably shouldn't say this too loud.  

<whispering> Why not download a Knoppix CD, which I know will just put the icons on the desktop for you? </whispering>

To answer your question.

```

su
fdisk -l
mkdir /mnt/whatever
mount -t ntfs /dev/hd? /mnt/whatever

```

Your files should be under /mnt/whatever at that point.

---

