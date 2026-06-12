---
title: "How to format Blu-ray disc for drag and drop"
date: 2014-01-02
forum: General Help
---

### Post by undoIT on 2014-01-02
I have a Blu-ray drive and some BD-RE DL 50GB discs that I want to use for backup. How do I format a disk so that it is automatically mounted and can be dynamically written to with drag and drop, like an external hard drive or USB drive? I have searched for a solution and haven't found one yet. I also tried formatting one of the discs in K3B. K3B now sees it as a "Complete Data BD-RE" but this does not seem to be what I need.

---

### Post by electrohandyman501 on 2014-01-02
I was able to google this:
[http://www.noobslab.com/2013/09/want-to-burn-all-kind-of-discs-blu-ray.html](http://www.noobslab.com/2013/09/want-to-burn-all-kind-of-discs-blu-ray.html)

If you got K3B thru the software center, according to the article, you didn't get all of the Blu-Ray tools. 

Not saying it's right or wrong, check it out yourself. YMMV.

---

### Post by Mark Phelps on 2014-01-03
Unfortunately, without special drivers (which are not made for Linux), you can't really treat an optical disk like a standard filesystem.

Some apps may claim they support "drag and drop" but what they really do is buffer that information in memory and don't actually change what's on the optical disk until you "save" the results.  They then, like all other apps, burn a "session" to the disk.

---

