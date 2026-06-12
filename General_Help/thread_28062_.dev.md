---
title: "/.dev ?"
date: 2005-04-18
forum: General Help
---

### Post by forcotton on 2005-04-18
Hi,
I've been using hoary since array1, there has been a /.dev all the time. is this a transitional thing and can be safely removed? I just don't see a reason why it's there...

---

### Post by diebels on 2005-04-18
Really? I have quite a few device files there. What does
ls /.dev
show you?

---

### Post by forcotton on 2005-04-18
There are more files than in the /dev directory. Look at this in /etc/fstab:
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)

/.dev seems to be some leftover... my real device file appears in /dev

---

### Post by diebels on 2005-04-21
I think /.dev is used by udev. It is created when you install udev. Removing it would stop udev from working properly.

---

