---
title: "Disable X?"
date: 2007-05-09
forum: General Help
---

### Post by xebitx on 2007-05-09
Hey

I just installed xubuntu on my server. I want it to run without any graphical user interface. How can I disable X from running on startup?

---

### Post by kuja on 2007-05-09
Easiest way would probably be to make it so xdm or gdm or kdm (whichever it is). Just go into /etc/rc[0-6].d/ (when I say 0-6, I mean there are 7 folders) and delete anything xdm, gdm, or kdm. those are just symlinks to scripts, don't worry, you're not deleting anything critical ... just symlinks.

Should you decide after startup that you want X to run, you just need to run the [x,g,k]dm script (whichever it is) that is in /etc/init.d/
ex: sudo /etc/init.d/kdm start

---

