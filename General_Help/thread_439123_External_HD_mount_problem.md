---
title: "External HD mount problem"
date: 2007-05-10
forum: General Help
---

### Post by Dearhell on 2007-05-10
When I mount my external HD I get this message:

> Volume is scheduled for check, please boot into windows TWICE, or use the force option ...

I have used the force option in the /etc/fstab the same way that it's detailed in the description but it didn't mount the external HD

Also, I don't have a windows system on my computer in order to boot twice

Any other way to fix this?

---

### Post by taurus on 2007-05-10
What filesystem is that external harddrive?

---

### Post by Dearhell on 2007-05-10
ntfs filesystem

---

### Post by taurus on 2007-05-10
If you don't have Windows anymore, why not format that harddrive to ext3 instead of using ntfs?  And even if you want to access it (ext3), you can always use [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by Dearhell on 2007-05-10
> **taurus said:**
> If you don't have Windows anymore, why not format that harddrive to ext3 instead of using ntfs?  And even if you want to access it (ext3), you can always use [http://www.fs-driver.org](http://www.fs-driver.org).

Because I have data in the HD that I want to access to

---

### Post by Dearhell on 2007-05-11
I have reinstalled Windows XP and mounted and umounted into Windows the external HD without any problem, but in Ubuntu I still get the same error message.

---

### Post by cryogenic on 2007-05-11
did you run chkdsk /f on the volume? You may need to do that in order for Ubuntu to really see that it's a clean volume.

---

### Post by Dearhell on 2007-05-11
I have tried that with the same results

I also tried disabling ntfs support on aplications tab and in that way the HD it's mounted, but I only have read access to it, if I enable ntfs support again, I get the same error message

---

