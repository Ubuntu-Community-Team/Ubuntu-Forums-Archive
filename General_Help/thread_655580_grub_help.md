---
title: "grub help"
date: 2008-01-01
forum: General Help
---

### Post by shadows123 on 2008-01-01
Hey!
i have this entry of grub..
it says my vista's on /dev/sda2..
but it's on my /dev/sda5...
sda 2's just a partition i keep my "important" files on ( it's more secure this way )
any idea what to edit in menu.lst?
i can do the rest..

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Well it should be dev/sda5.. but idk what all that means lol..
i know i have to do sudo update-grub & etc..
Thanks in advance!

---

### Post by jken146 on 2008-01-01
Can you boot into Vista?  If not, then change (hd0,1) to (hd0,4).

---

### Post by kshane on 2008-01-01
... And make sure your fstab agrees with menu.lst...

Kevin

---

### Post by shadows123 on 2008-01-02
Hmm
i can't boot in it yeah. i get f12 msg..
and.. yea i tried hd(0,4) there and didn't work.. well i will try again in some time ( as i'm not on my pc atm )
[tried 0,4 & 0,5 both aren't working]
:|

==> What's fstab?

---

### Post by shadows123 on 2008-01-04
please, anyone?

---

### Post by Nunu on 2008-01-04
Basically 

**fstab** is a configuration file and is used to tell the kernel what drives (technically [filesystems]("http://wiki.linuxquestions.org/wiki/Filesystem")) to [mount]("http://wiki.linuxquestions.org/wiki/Mount") and where.

There is some more info [here]("http://wiki.linuxquestions.org/wiki/Fstab")

---

