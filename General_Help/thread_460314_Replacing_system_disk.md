---
title: "Replacing system disk"
date: 2007-05-31
forum: General Help
---

### Post by koma77 on 2007-05-31
I have Ubuntu running on a single HD in my computer.

I want to replace this HD with a new, bigger one and I really want to remove the old one.

I want to run from one HD only.

How can I transfer the whole installation and still have a nice bootable new HD in the end?

---

### Post by jamesjtucker on 2007-05-31
The easist way to do this is to use a disk imaging/cloning program. there are a number of programs to do this, Norton Ghost being the first one that comes to mind, but that costs money. And no one likes that :)
  A quick search shows a lot of linux based utilities to do this, the most promising looks to be 
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)  which might be exactly what you need, but i have not used it so cannot vouch for its effectiveness. I also found these instructions, which seems to be a pretty good method: 
[http://www.pccitizen.com/driveimage.htm#5](http://www.pccitizen.com/driveimage.htm#5)

Let us know your results!

---

### Post by ajgreeny on 2007-05-31
There's also partimage which does the same, ie makes a clone of yopur partition which you can then restore to another hard drive.  It is on the gparted live CD which you can easily download.  Just google for it; it's only about 30MB download and is also great as a partition manager.

---

### Post by jamesjtucker on 2007-05-31
DOH, forgot about gparted! I literally have a copy sitting about 1 foot from my keyboard as well :D

---

### Post by koma77 on 2007-05-31
But a perfect clone would include the original MBR, and doesn't that include things like the size of the disk. Which would show up as my old drives size... Which is wrong...

---

