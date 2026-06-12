---
title: "Grub help"
date: 2008-04-01
forum: General Help
---

### Post by kingleer on 2008-04-01
I'm trying to get grub to recognize OS X 86 by editing my menu.lst file

from looking at here

[http://forum.insanelymac.com/index.php?showtopic=75978&pid=536533&mode=threaded&start=#entry536533](http://forum.insanelymac.com/index.php?showtopic=75978&pid=536533&mode=threaded&start=#entry536533)

I figured out you need to do something like this

> 
title Mac OSx86
root (hd1,0)
savedefault
makeactive
chainloader +1


My question is what do i put in place of (hd1,0)? 

Thanks

---

### Post by Kevbert on 2008-04-01
hd(1,0) refers to the second hard disk, but first sector- the first hard disk, first sector would be hd(0,0) as it's  all numbered from zero.  You'll need to adjust this for your OS.

---

