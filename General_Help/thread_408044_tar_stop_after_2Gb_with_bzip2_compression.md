---
title: "tar stop after 2Gb with bzip2 compression"
date: 2007-04-12
forum: General Help
---

### Post by Biochem on 2007-04-12
I want to backup my file system. I tried to use tar with the bzip2 or gzip compression. However everything stop after 2Gb ressulting in an incomplete corrupted file. I know I can't use the multiple volume option while using compression so I cannot split the file. 

Is there any work around, other program, that I could use? 

Also for pure curiosity why is there a 2Gb file size on many copression algorythm?

---

### Post by JensenDied on 2007-04-12
FAT32 filesystems cannot have files larger than 2gb, try splitting the files.

---

### Post by Biochem on 2007-04-12
Thanks JensenDied,
However, the destination drive also contain file larger than 4Gb so my guess is that it is not the issue here.

---

### Post by dcstar on 2007-04-12
> **Biochem said:**
> Thanks JensenDied,
However, the destination drive also contain file larger than 4Gb so my guess is that it is not the issue here.

If the file was created by Windows then maybe not, I believe the Linux FAT32 driver has a 2GB limitation.

---

### Post by Biochem on 2007-04-12
Well seems like there is effectively a size limit on my network drive that wasn't there with windows.

Now is there a way to split the file on the fly? Tar won't allow to split compressed file. :(

---

### Post by dmizer on 2007-04-13
network drive?

is the destination for the tar ball a mounted windows network drive?  if that's the case, your cap is a result of smbfs, not of the fat32.  you can get around this by using cifs instead of smbfs.  howto for cifs in the second link in my sig.  it will allow for larger network file transfers.

apologies if i've mistaken what you're doing.

---

### Post by Biochem on 2007-04-14
You were right dmizer it was indeed a smbfs problem. Thanks for the how to.

---

### Post by RJARRRPCGP on 2007-04-14
> **JensenDied said:**
> FAT32 filesystems cannot have files larger than 2gb, try splitting the files.

That's incorrect. It's 4 GB. Make sure that it's not FAT16! 

FAT16 is so 1990s and as much as I liked some of the 1990s, it's time to move on!:wink:

---

