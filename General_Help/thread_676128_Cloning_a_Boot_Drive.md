---
title: "Cloning a Boot Drive"
date: 2008-01-23
forum: General Help
---

### Post by Xavior on 2008-01-23
I am replacing my 40gb drive with a 80gb drive,
How do I make a clone of my 40gb to the 80gb so I can remove the 40gb ?

I tried True Image, but on the new drive boot, all I see is the word GRUB...

thanks,
Xav

---

### Post by julian67 on 2008-01-23
The best Free open source tool for cloning drives is [Clonezilla]("http://clonezilla.sourceforge.net/"). It's a live CD which also has GParted on it so it's a complete solution for you. You can clone your old disk onto the new one, complete with MBR, and then use GParted to expand/further partition your drive as required.

---

