---
title: "reinstall GRUB"
date: 2007-08-01
forum: General Help
---

### Post by atlfalcons866 on 2007-08-01
hi
I installed windoze xp because i cant live with out a game i play. How do i reinstall Grub?

---

### Post by DeclanMcErlane on 2007-08-01
Mkay, put in your Ubuntu Live CD and start on boot-up.

Go to terminal and type

```
 sudo grub 
```

Type your password afterwards then type

```
 find /boot/grub/stage1
```

Yuo should receive an output similar to (hd0,1) or (hd0,2) depending on your hard-drive setup

Whichever ne you receive back type 

```
 root ("the output you received from the latter command")
setup ("the same output again")
```

Hopefully that should restore your GRUB Loader

Declan

---

### Post by merlinus on 2007-08-01
First of all, the forum search feature works wonders!

Boot from the live cd, and at a terminal enter:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute your results for (hdx,x).  If you have one hard disk and ubuntu is on the second partition, then it will most likely be:

root (hd0,1)
setup (hd0)

-merlin

---

### Post by DeclanMcErlane on 2007-08-01
Hey merlin thanks for the correction. I knew I had gone wrong somewhere ;)

---

### Post by bodhi.zazen on 2007-08-01
> **merlinus said:**
> 

root (hd0,1)
setup (hd0)

-merlin

Thanks for saving me a little typing ...

---

