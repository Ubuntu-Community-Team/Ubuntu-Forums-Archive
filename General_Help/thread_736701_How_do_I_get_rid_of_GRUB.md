---
title: "How do I get rid of GRUB?"
date: 2008-03-26
forum: General Help
---

### Post by ubuntu1sttimer on 2008-03-26
I put a 7.10 live disk into a WIN  98 machine and tried to check to be sure the disk was good. That did not work and now I get a message saying:

GRUB loading 1.5.

GRUB loading, please wait......
Error 17

The Ubuntu disk does not load, Windows does not load. 

How do I get GRUB off the hard drive and restore the original OS without reformating the HD?

---

### Post by nick_h on 2008-03-26
You need to boot from a Windows CD and then go into recovery mode.

Then you either need to type:
```
fixmbr
```
or
```
fdisk /mbr
```
to restore the Windows MBR.

I forget which to use for Win 98 (I think fixmbr might just be for XP and Vista).

---

### Post by giants_fan on 2008-03-26
Also, if you don't have a Windows disk lying around, you can use FreeDOS ([http://www.freedos.org](http://www.freedos.org)).  It comes with it's own version of fdisk.  I found myself in a similar situation (wanted to remove GRUB) on a computer a few weeks ago and FreeDOS worked like a charm.

---

### Post by capink on 2008-03-27
You can also restore it [using ubuntu live cd]("http://ubuntuforums.org/showthread.php?t=622828").

---

### Post by forrestcupp on 2008-03-27
> **capink said:**
> You can also restore it [using ubuntu live cd]("http://ubuntuforums.org/showthread.php?t=622828").
Wow!  That's cool.  I didn't know you could do that.  I may stop suggesting [Super Grub](http://supergrub.forjamari.linex.org/) now.


If you can't even boot to your Ubuntu Live CD, you need to make sure that your bios is set to boot to CD 1st.

---

### Post by Oldsoldier2003 on 2008-03-27
> **forrestcupp said:**
> Wow!  That's cool.  I didn't know you could do that.  I may stop suggesting [Super Grub](http://supergrub.forjamari.linex.org/) now.


If you can't even boot to your Ubuntu Live CD, you need to make sure that your bios is set to boot to CD 1st.

I may have to play around with it, but I still think I'll recommend supergrub because its a little less work and in most cases a no brainer recovery tool.

---

### Post by ubuntu1sttimer on 2008-03-27
Thanks all for the great help. 

I used a WIN 98 system install disk that allowed me the choice of a DOS prompt. Did the fdisk /mbr command and it worked. Have a lot of information on the old machine. Until I can get Samba and this old machine talking I would be very unhappy if I lost it all.

Also found that MS has a documentation page on fdisk /mbr in case anyone else needs it.

Again, thanks.

---

