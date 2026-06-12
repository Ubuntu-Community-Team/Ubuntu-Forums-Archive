---
title: "usplash theme looks really ugly (pic) - wrong resolution?"
date: 2007-04-08
forum: General Help
---

### Post by strabes on 2007-04-08
After the update to kernel 2...14 my usplash theme looks like crap. I attached a pic. Maybe it's the wrong resolution? Here's the relevant part of my menu.lst:

> 
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-14-generic root=UUID=09d2e5f8-c128-4244-b2ba-6259c0515588 ro quiet splash vga=791 resume=/dev/sda6
initrd          /boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-14-generic root=UUID=09d2e5f8-c128-4244-b2ba-6259c0515588 ro single
initrd          /boot/initrd.img-2.6.20-14-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by jimbob on 2007-04-08
Try taking that vga=791 out of the kernel line.  Did you put that in there?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

 *[SIZE="1"]... when the game is over the king and pawn go in the same bag ...[/SIZE]*

---

