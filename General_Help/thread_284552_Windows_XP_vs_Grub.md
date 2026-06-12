---
title: "Windows XP vs Grub"
date: 2006-10-25
forum: General Help
---

### Post by pandemic on 2006-10-25
Here is my setup:

I have Ubuntu 6.06 LTS on hard drive 1(master), and Windows XP on hard drive 2 (slave). I have placed an entry in my menu.lst file that looks like this.

```

title		Windows XP W/ Service Pack 2
rootnoverify	(hd1,0)
chainloader	+1
makeactive

```

When I boot and select "Windows XP W/ Service Pack 2" from the menu all I get is a screen that says:

```

Booting Windows XP W/ Service Pack 2

title		Windows XP W/ Service Pack 2
rootnoverify	(hd1,0)
chainloader	+1
makeactive

```

What am I doing wrong???

---

### Post by ~LoKe on 2006-10-25
> title		Microsoft Windows
root		(hd1,0)
savedefault
makeactive
chainloader	+1

Try that.

---

### Post by pandemic on 2006-10-28
Thanks for the reply, but I tried that and nothing changed. I still haven't been able to find a solution, but I've read that windows doesn't like to be to on a slave drive. If this is the case does anyone know how to get windows past its pride?

---

### Post by Spano on 2006-10-28
A suggestion: 

title           Other operating systems:

title           Windows XP
root (hd1,0)
map  (hd0) (hd1)
map  (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

See this page - section 4.2.6 
[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by galileon on 2006-10-28
i seem to remember windoze wants to be the first hdd, so have you tried putting it first? did this particular configuration work before?

---

