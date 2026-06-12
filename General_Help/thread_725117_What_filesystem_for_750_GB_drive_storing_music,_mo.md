---
title: "What filesystem for 750 GB drive storing music, movies, and pics?"
date: 2008-03-15
forum: General Help
---

### Post by jsprag on 2008-03-15
I'm adding a 750 GB SATA internal drive to store media files and not sure what the best choice for file system would be.  Music is a mix of MP3 and FLAC, and movies are all AVI's between one and three GB.

System is 7.10 server AMD64 running on AMD 64 X2 4000 with 2GB of RAM.

From my reading it seems like either EXT3 or XFS is most appropriate.  Thoughts?

Thanks,
John

---

### Post by PmDematagoda on 2008-03-15
Personally I would recommend Ext3, it is more reliable than XFS though it maybe slower but would be something you may be willing to pay when you consider your use.

---

### Post by articpenguin on 2008-03-15
Try JFS

JFS is more reliable than xfs but a little less than ext3 on hard power offs. JFS also handles large files better than ext3. Also ext3 has an annoying fsck.

---

