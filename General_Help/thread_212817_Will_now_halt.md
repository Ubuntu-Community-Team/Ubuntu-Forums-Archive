---
title: "Will now halt"
date: 2006-07-10
forum: General Help
---

### Post by huwnet on 2006-07-10
For someone reason Ubuntu doesn't automatically switch off. It gets to "Will Now Halt" but doesn't automatically switch off.

Any way of fixing this?

TIA

---

### Post by hellmet on 2006-07-10
I am not sure but..I think its got something to do with BIOS..
just have a look at POWER settings for your BIOS..
see if therez anything u think wud turn that thing off!!

---

### Post by hellmet on 2006-07-10
[http://ubuntuforums.org/showthread.php?t=189498](http://ubuntuforums.org/showthread.php?t=189498)
see this

---

### Post by hellmet on 2006-07-10
POSTED BY PETER76

I had the same problem, think it has to do with with older hardware and the newer Dapper kernel.
To solve it, edit your /boot/grub/menu.lst and pass "acpi=force" and "lapic" to the standard kernel as arguments. Save the file, run: sudo update-grub, and reboot. It should shutdown and restart fine now.

Here's my entry in my /boot/grub/menu.lst ( it's near the end of the file ) :

title Ubuntu, kernel 2.6.15-23-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force lapic
initrd /boot/initrd.img-2.6.15-23-686
savedefault
boot

Good luck, and hope this helps.

PS: It is possible you only need to pass one of the options; there's a bell ringing somewhere that I needed one of them for something else, but not sure anymore. Try and post your results, so others can benefit as well.


all the best!!

[http://ubuntuforums.org/showthread.php?t=187186&page=1](http://ubuntuforums.org/showthread.php?t=187186&page=1)

---

### Post by huwnet on 2006-07-10
The workaround did allow the system to shutdown correctly however I need some options (noapic acpi=off) in order to get the correct graphics resolution and for the network card to function correctly.

Is there some sort of workaround which will allow shutdown, graphics and the network card to all work correctly?

---

