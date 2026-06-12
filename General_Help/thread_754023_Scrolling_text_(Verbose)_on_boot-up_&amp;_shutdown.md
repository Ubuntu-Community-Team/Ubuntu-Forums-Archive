---
title: "Scrolling text (Verbose) on boot-up &amp; shutdown - how to remove?"
date: 2008-04-13
forum: General Help
---

### Post by meuge on 2008-04-13
I shrunk and grew some partitions using Gparted, and now I get a verbose boot-up/shutdown (the orange progress bar disappears after a couple of sec of going back and forth, and then is replaced with the scrolling text of the verbose boot). 

The boot-up process completes fine and loads my system fine. 

The "quiet" boot option is already enabled in /boot/grub/menu.lst
> title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=04af32aa-9d78-4b85-b1ba-a303d9500dcd ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet


What can I do to make it go away?

---

### Post by Ptero-4 on 2008-04-13
run fsck -y from the LiveCD. It might fix things up a bit (usplash is very sensitive to warnings and errors at boot time and at the first one that shows up it just bails out).

---

