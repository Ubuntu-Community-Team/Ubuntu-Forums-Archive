---
title: "Rescue Mode is not working, I need help!"
date: 2006-11-05
forum: General Help
---

### Post by Beowulf.1000 on 2006-11-05
I am having problems with the rescue mode of Ubuntu. I boot the "Ubuntu 6.10 i386 Alternate" CD, which as "Rescue a Broken System" as an option upon boot off the CD. Ok, so I choose the rescue option, say yes to English, etc, then it wants to know where the root filesystem is, so I tell it /dev/hda6 (previously determined from the 'df' command in a terminal). Then I choose the option to 'Reinstall GRUB Bootloader" and am asked where to install GRUB, e.g. /dev/hda, etc. Knowing (from 'df') that WindowsXP is on /dev/hda1 I type that into the input line, press Enter
key, and get  "**The rescue operation 'grub-reinstall' failed with exit code 20**."

I click go back and try /dev/hda and get the same thing. I tried (hd0), I tried (hda0,0) and keep getting the same error.  I am quite lost as to how to use the rescue mode of the Ubuntu Alternate live CD; if anybody has some
ideas or thoughts I am open.

---

### Post by an.echte.trilingue on 2006-11-05
I had to do that once, and I think grub goes on the MBR located at /dev/hda0 or /dev/hda.

Good luck,

-mat

Edit: oops missed the end of your post... sorry, i'm stumped too.

---

### Post by Beowulf.1000 on 2006-12-20
> **an.echte.trilingue said:**
> I had to do that once, and I think grub goes on the MBR located at /dev/hda0 or /dev/hda.
Edit: oops missed the end of your post... sorry, i'm stumped too.

I finally figured it out., Wrote a little text file on restoring GRUB, worked for me-- I tried it on a laptop and PC running Ubuntu just to know it works:

GRUB RESTORE/FIX HOW-TO
If you use the GRUB bootloader which is common with Ubuntu and some other 
distributions, you might find an occasion when it is overwritten such as
if you reinstall MS-Windows. This is a quick guide on restoring the grub
bootloader to your MBR in such a situation.

Insert Ubuntu Live (install) CD into CD drive and restart computer
When Ubuntu CD boots up, just press Enter to choose boot/install Ubuntu
After several minutes, Ubuntu live CD will show linux desktop, then
choose Accessories=> Terminal from menu

#  sudo -i
#  grub

This will invoke grub and you will see a '>' prompt

  >  find /boot/grub/stage1

You will see something returned to you like (hd1,0) and write that
down! Let's say it returns to you the value (hd1,0). If you get (hd1,1) 
or whatever use that instead of (hd1,0). Note that there *is* a space 
between root or setup and the ( symbol and no spaces within the 
parentheses. root () tells grub where kernel resides. setup () tells
grup where to install grub.

  > root  (hd1,0)
  > setup (hd0)
  > quit

# shutdown -r now
  (or just choose shutdown from menu) 
Remove CD.
Reboot.

---

### Post by springblue on 2008-06-12
Thanks.  I was getting the "exit code 20" error.  Your write up solved the problem for me.
Cheers!

---

