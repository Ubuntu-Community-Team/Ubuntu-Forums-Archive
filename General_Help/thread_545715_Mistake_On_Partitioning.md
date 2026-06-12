---
title: "Mistake On Partitioning"
date: 2007-09-07
forum: General Help
---

### Post by GatorGreen on 2007-09-07
Hello,

I decided to install Ubuntu, but I messed up on the partitioning part. Instead of choosing how much I wanted to leave for Windows, I chose the amount I wanted to use for Ubuntu. So now I have 20GB for Windows and 80GB for Ubuntu. Is there any way I could make the Windows partition largest again without reformatting the entire hard drive?

Thanks in advance.

---

### Post by merlinus on 2007-09-07
Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by strabes on 2007-09-08
Why don't you leave windows as 20 gb, shrink ubuntu to 15 or less, and use the rest for a data partition? That's what I do and it works great!

---

### Post by GatorGreen on 2007-09-08
> **merlinus said:**
> Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

Thanks! It successfully shrunk Ubuntu, but it won't allow me to make the Windows partition any larger. I think this is because Ubuntu is between Windows and the unused data. How would I make the Windows partition larger?

> **strabes said:**
> Why don't you leave windows as 20 gb, shrink ubuntu to 15 or less, and use the rest for a data partition? That's what I do and it works great!

I might try leaving some room for a data partition if I can get everything working. I will probably need more than 20GB for some programs I will be installing soon though. Thanks!

---

### Post by merlinus on 2007-09-08
Perhaps you should have shrunk the ubuntu partition from left-to-right, so the free space could be added to windows.

-merlin

---

### Post by rsambuca on 2007-09-08
I think you might have a couple of options.

1.  Try gParted and "move" the ubuntu partition first.  Then expand the Windows partition.

2.  Probably the easiest option is to add another ntfs partition to the end so that Windows can use it.  Then make a new folder for programs on that partition so that you can install your Windows programs there, if you need more room (But more than 20GB??).  You can then use the ntfs-3g package for ubuntu so that you can read/write to the new drive as well.

---

### Post by GatorGreen on 2007-09-08
> **merlinus said:**
> Perhaps you should have shrunk the ubuntu partition from left-to-right, so the free space could be added to windows.

-merlin

> **rsambuca said:**
> 
1.  Try gParted and "move" the ubuntu partition first.  Then expand the Windows partition.


I got it to work by doing what you both suggested. 

Thanks to everyone who posted.

---

### Post by merlinus on 2007-09-08
Gotta love those success stories.  Glad it worked!

-merlin

---

