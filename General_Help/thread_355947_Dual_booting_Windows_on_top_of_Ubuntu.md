---
title: "Dual booting Windows on top of Ubuntu"
date: 2007-02-07
forum: General Help
---

### Post by MeathooK427 on 2007-02-07
Well, I guess I want to know how to do this! I installed Ubuntu a few months back, and been messing with it, and now just today installed XP onto the 2nd partition. How do I set my MBR to accept both?? Has anybody done it this way? Most of the tutorials I see are from scratch, with Windows first, then Ubuntu. Any help would be greatful

Thanks

---

### Post by DagMan on 2007-02-07
I'm not sure if this is okay or if it needs something special.  I haven't grubbed into windows in ages and always had it on the first partition, but try this out to see:

```
title		Windows 95/98/NT/2000
root		(hd0,1)
makeactive
chainloader	+1
```
The change is (hd0,1) instead of (hd0,0) in the line that says root.
The chainloader line might need something extra too... I don't undertand that part.  It shouldn't hurt anything to try it as I posted though

Hope it works :)

---

### Post by MeathooK427 on 2007-02-07
Well, I'm in Windows at the moment, I suppose I can boot into Linux w/ my CD and try that. What file was that?

---

### Post by logos34 on 2007-02-07
Why don't you restore grub to the mbr first, then boot into Ubuntu and  add a win entry to menu.lst

If you have the alternate install cd, boot from it and select repair broken system from the menu.  Then choose restore/reinstall grub option.

If you have the livecd, boot from it and load the desktop.  Open a terminal and type the following commands:
> 
sudo grub
root (hd0,0)    (*assuming / is hda1)
setup (hd0)

Reboot into Ubuntu and add winxp entry to grub:

> gksudo gedit /boot/grub/menu.lst

Add to the end

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows XP
root            (hd0,1)   (*or **rootnoverify (hd0,1)**)
makeactive
chainloader     +1

---

### Post by MeathooK427 on 2007-02-07
Thank you, I'll try that shortly.

---

### Post by MeathooK427 on 2007-02-07
Well, I'm back into Ubuntu now, and modified the menu.lst and added what you specified (copy and pasted), and it comes back and gives me this error:

Error 13: Invalid or unsupported executable format...Press any key to continue

Any ideas?? The Windows XP install is on the same hard drive...so I don't know if that would modify the code or not. 

Thanks!

---

### Post by MeathooK427 on 2007-02-07
Problem fixed: Had to change hd0,1 , to hd0,2 since it's the 3rd partition on the disk. 

1. Linux
2. Swap
3. NTFS

Thanks for all ya'lls help. It's much appreciated :)

---

### Post by NoobieDoobieDo on 2007-02-13
[http://tehpost.blogspot.com/2007/02/grub-booting-windows-xp-using-grub.html](http://tehpost.blogspot.com/2007/02/grub-booting-windows-xp-using-grub.html)

^ Is how I ended up having to do it.  Works like a charm for me.

My setup is

hd0 - linux
hd1 - windows xp

---

