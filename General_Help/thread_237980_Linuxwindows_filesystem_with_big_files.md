---
title: "Linux/windows filesystem with big files?"
date: 2006-08-17
forum: General Help
---

### Post by Face1 on 2006-08-17
Hi I have a dual boot computer, and an external HD.  I haven't yet formatted the HD, and I'm trying to decide what filesystem to use.  I would like to have it read/writable in both windows and linux, and I'm not willing to take risks writing to ntfs with linux.  Also, I can't use ext3 with the ext2ifs windows support, because that only supports reading. That would leave FAT32.  However, FAT32's maximum file size is 4 gigs.  I would like to be able to rip DVDs to this drive, which can be 4.7 gigs (Also, I will likely have other unrelated >4gig files, so compressing the video or what have you is irrelevant).  Is there some other filesystem I could use?  What about [http://en.wikipedia.org/wiki/Universal_Disk_Format]("http://en.wikipedia.org/wiki/Universal_Disk_Format")?  Sure it isn't traditionally used on HDs, but why not?  Both Win & Linux support it, and it can have files far bigger than any HD I could ever hope to own!

---

### Post by catlett on 2006-08-17
You are wrong abput the ext2 driver. It supports read and write to ext3. You just loose the journaling when accessing from windows.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
```
Complete reading and writing access to files and directories of volumes with the Ext2 or Ext3 file system.
Files larger than 4 GBytes.
```

---

### Post by Face1 on 2006-08-17
I stand corrected, I was 100% wrong.  I had been looking at a [different site]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm"), for something that I guess is a different project.  Thanks for the link, I'm going to try it out right now.

---

### Post by catlett on 2006-08-17
No problem. I just didn't want you to miss out on an easy solution to your problem.
Take care.

---

### Post by Ramses de Norre on 2006-08-17
Since ext3 is open source it would be pretty weird if no one was able to write a windows r/w driver, wouldn't it ;)

---

