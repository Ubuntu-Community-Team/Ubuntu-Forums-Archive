---
title: "External Hard Drive in Windows XP"
date: 2008-06-20
forum: General Help
---

### Post by ABD101 on 2008-06-20
I installed Ubuntu 8.04 onto my WD 80GB external hard drive and it works great. But when I go back into windows xp and look im my computer, the external hard drive does not show up. It is present in my device manager, but not in my computer.

What could be the possible problem.

---

### Post by logos34 on 2008-06-20
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ajgreeny on 2008-06-20
Yes, windows is not as clever as ubuntu and other linux distros, so it can't see linux unless you add some third party utilities.  Beware, however, of using them to write to a linux partition, as I've heard that it can mess up the linux file system in some way.  I have no experience of this, however, I'm just passing on comments I have read somewhere else.

---

### Post by ABD101 on 2008-06-20
Is there a way that I can reformat the drive, partition the hard drive so that 40GB is for ubuntu and 40GB is for storage?

---

### Post by logos34 on 2008-06-20
> **ABD101 said:**
> Is there a way that I can reformat the drive

all you need to do is resize/shrink ubuntu /, then create another ext3 partition ('storage').  Use Gparted on the ubuntu livecd.

---

