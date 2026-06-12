---
title: "System time being reset? Dual boot XP &amp; Feisty"
date: 2007-04-02
forum: General Help
---

### Post by cgrucelski on 2007-04-02
Hey all.

I have a system with (2) separate IDE hard drives, one with latest Feisty build (which I LOVE!) and the other with XP SP2. I edited the grub menu.lst as follows:

[I][INDENT]title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/INDENT][/I]

Both systems boot and function perfectly, except one minor little annoyance. The problem that I am experiencing is that on the occasions when I need to log out of Ubuntu and boot back into XP, the system time within XP is always reset to the wrong time... the offset is several hours (I believe it may be 5... the amount my location differs from UMT).

Any ideas as to why this is occurring and how to prevent this? Thanks in advance.

---

### Post by jasutton on 2007-04-02
I'd make sure your timezone is set correctly in both OSes.  This definitely sounds like the sort of problem you'd see if one or the other was set incorrectly. ;)

---

### Post by confused57 on 2007-04-03
This should fix your clock problem:
[http://www.ubuntuforums.org/showpost.php?p=698200&postcount=5](http://www.ubuntuforums.org/showpost.php?p=698200&postcount=5)

---

### Post by cgrucelski on 2007-04-03
Cool!

Thanks for the info... I will try the suggested solution and post back if it is not successful.

Thanks,

---

