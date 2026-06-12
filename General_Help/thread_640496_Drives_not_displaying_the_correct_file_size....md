---
title: "Drives not displaying the correct file size..."
date: 2007-12-14
forum: General Help
---

### Post by mxd208 on 2007-12-14
Not sure what's going on here...and I should preface this with "I am a newbie..."

But, I have a 4GB USB flash drive that I can browse in Windows and see that it has about 2.3 GB available....however, when I mount the drive in Ubuntu, it shows that I have 295mb available...and then it protects the drive so that I can't write to it anyway.

I also have my internal hard drive partitioned for dual booting, and I have the same issue with my Windows partition.  I have about 6gb available there, and it only shows about 800MB available.  Any thoughts on what's going on?

Does it matter if I'm deleting/removing data from those drives outside of Ubuntu?  Does Ubuntu not know what's happened in Windows and remember what it was earlier?

How do I get the drives to read correctly?

---

### Post by vanadium on 2007-12-14
The behaviour you describe for your USB  (especially the "protect the drive" part) leads me to suggest that you need to check the file system of your USB. The same might cause your issue with your Windows partition, but here I am less sure: an ntfs partition that is not OK normally refuses to mount, while you can mount it.

---

### Post by mxd208 on 2007-12-14
how about the drive size reading incorrectly?  Any thoughts there?  

The protecting the drive part is sporadic...only happens sometimes.  The drive size happens all of the time.

---

### Post by vanadium on 2007-12-14
According to me, the wrong free size reported is due to the file system that is damaged and needs to be checked. Check the file systems and see weather the issue persists. A file system should be checked periodically anyway, so you cannot do harm.

---

### Post by mxd208 on 2007-12-14
How do I check the file system of the USB?

---

### Post by vanadium on 2007-12-14
unmount the drive first, then you can check it using the fsck command.

---

