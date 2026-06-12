---
title: "startup/shutdown problems"
date: 2006-11-06
forum: General Help
---

### Post by captainsolo on 2006-11-06
I installed Edgy on my PC and it works well most of the time except for when I start it up and turn it off. Some times when I start Edgy it gets to the Ubuntu loading bar and then the screen just goes blank. It doesn't do this every time. Does any one know what is going on?

Also the PC doesn't turn off at the end of the shutdown but instead goes to a blinking cursor and I have to press the button to turn it off. Does anyone know how to make it so that Ubuntu turns the PC off?

Thanks.

---

### Post by goodfella on 2006-11-06
I had the same problem at shutdown.  In my /boot/grub/menu.lst file I had to use the acpi=force option.  Here is an example:

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hdb2 ro quiet splash acpi=force
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

Hope this works.

---

