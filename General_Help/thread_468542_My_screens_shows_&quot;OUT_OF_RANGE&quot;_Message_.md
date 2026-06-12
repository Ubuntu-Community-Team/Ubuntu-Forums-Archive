---
title: "My screens shows &quot;OUT OF RANGE&quot; Message During Boot time"
date: 2007-06-09
forum: General Help
---

### Post by alexrait1 on 2007-06-09
When the computer boots with ubuntu, my LCD screen shows the following message:
OUT OF RANGE
35.4Hz/43Hz

When it loads GDM then everything is being shown correct.

What should I change to make it right?

---

### Post by benner on 2007-06-09
mine does too.  i just assumed it was normal.  mine is a BenQ FP92W.  I had to modify my xserver-xorg to add the monitor's resolution.  and I couldn't get the full resolution (1400 x 900 I think) using the open source driver or the screen turned green. But even when I use the fglrx driver (my video card is an ATI x550) I get the full resolution but still get the 'OUT OF RANGE' messages at boot.  Thanks for bringing it up.  I guess it is annoying.

---

### Post by scarboni on 2007-06-11
I had this problem but worse with the 64-bit.  If you add the 'nosplash' option to the kernel option you'll be able to see feedback during the bootup - just no fancy ubuntu splash screen with the orange bar going across it.  In the 64-bit version it's apparently a bug in vesa because on the same exact equipment the 32-bit version works fine for the splash screen.

---

### Post by Nythain on 2007-06-11
you can gksudo gedit /boot/grub/menu.lst
and add vga=792 after the two occurances of quiet splash (or splash quiet)
one occurance should be at a line that starts
#defaultsomejunk
and the other should be down where it lists the different boot options/kernels

save the file and try again... if just adding the vga=792 doesnt help, then as far as i know, the only other solution is to delete the two occurances of quiet splash (or splash quiet)

but you will no longer have a pretty usplash screen (wich you dont have anyways so no big loss eh)

---

### Post by wpshooter on 2007-06-11
I am having this same "out of range" problem on one of my machines.

This is when I am attempting to install Gutsy Tribe 1.

This same machine does not do this on either Dapper, Edgy or Feisty.

My card is an ATI Radeon 9200 and monitor is Viewsonic LCD - model VA702b

Why should it be necessary to add this VGA=792 line in the GRUB on a Gutsy install when this was not necessary on previous versions of the Ubuntu O/S ?

Thanks.

---

### Post by alexrait1 on 2007-06-22
If anyone is interested, my screen shows the boot process only when I change the
vga option to vga=787. Neither 791 nor 792 nor 790 do not work for me....

---

