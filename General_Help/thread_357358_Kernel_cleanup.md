---
title: "Kernel cleanup"
date: 2007-02-09
forum: General Help
---

### Post by Adam Atlas on 2007-02-09
My Ubuntu server has been running since 2005 and, therefore, has gone through several Ubuntu versions... I think it started on Hoary or Breezy. Naturally, by now, it's gone through a whole lot of kernel versions, complicated further by my use of custom-compiled kernels for Xen and such. So my /lib/modules and /boot directories have gotten really cluttered. Is there a safe, standard way to remove all the files associated with a particular kernel version/build? I don't even remember what "2.6.12-skas3-v9-pre7" was, for instance, but I know that I'm sure not using it now. I suppose I could just do something like rm -rf `find /boot /lib -name \*2.6.12-skas3-v9-pre7`, but I just wanted to make sure I'm not overlooking a better(/cleaner/safer?) way.

---

### Post by nitsnipe on 2007-03-03
I have a similar problem as well, 
I heard that feisty was going to come with a system clean-up tool  but on the live cd the tool is nowhere to be seen.

Hopefully someone helps us

---

### Post by victorgreen on 2008-01-26
Yeah that would really be nice to know, from what ive read it could solve my utterly insane, persistent and sustained sound headaches if I could clean out any old kernels installed on this thing.

---

