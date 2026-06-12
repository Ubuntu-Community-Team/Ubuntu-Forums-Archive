---
title: "Can't boot to windows"
date: 2008-02-08
forum: General Help
---

### Post by Achenar on 2008-02-08
Hi,

I've recently installed Ubuntu 7.10 64-bit in my main machine. I have Windows XP in the same drive, and I've actually got to boot it several times before it suddenly stopped working. Now when I select Windows in the grub menu, it tells me something about 'stage2' and returns to the OS selection menu.

My Windows entry in \boot\grub\menu.lst is:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

sudo fdisk -l gives me:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104864256    7  HPFS/NTFS
/dev/sda2           13056       52218   314576797+   7  HPFS/NTFS
/dev/sda3           52219       58746    52436160    7  HPFS/NTFS
/dev/sda4           58747       60801    16506787+   5  Extended
/dev/sda5   *       58747       60709    15767766   83  Linux
/dev/sda6           60710       60801      738958+  82  Linux swap / Solaris

I really need to boot windows. What should I do?

Thanks

---

### Post by alan34 on 2008-02-09
Could try this seen it recommended many times but I have never tried it myself.


[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

burn the ISO and set your PC to boot from the CD drive

Good Luck

Just tried using it to boot my windows partion and ended up in my Dell Hardware driver partion 

so its not for the faint hearted. Read the documentation might be a good idea first.

Good luck again

---

### Post by sandysandy on 2008-02-09
are u able to boot ubuntu. is it only windows that is not booting.

what is the exact error which comes

also have a look at this

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

regards

---

