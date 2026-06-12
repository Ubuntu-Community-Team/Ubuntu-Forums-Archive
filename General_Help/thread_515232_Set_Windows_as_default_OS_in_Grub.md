---
title: "Set Windows as default OS in Grub"
date: 2007-08-01
forum: General Help
---

### Post by Greensauce on 2007-08-01
Hi I use Windows as a Primary OS (yes i know i suck) but I am still learning Ubuntu and don't want to "dive in" yet. When I restart my computer GRUB automatically see's Ubuntu as the default and I have to scroll down to Windows Vista/Longhorn. Is there a command or a way I can set it as default on Windows?

---

### Post by DeclanMcErlane on 2007-08-01
Yeah, I had the same problem a while ago but I sorted it by doing this. Go to terminal and type

```
sudo gedit /boot/grub/menu.lst
```

Scrolling down near the bottom you will see the list of options presented at your GRUB loader. Now remember the number of your XP OS. Scroll upwards again and look for "default 0". Change this to "default (number of XP selection in GRUB Loader)". Then click save. It is also possible to change the timeout if you want a longer/shorter period of time to wait before the OS boots by going to "timeout 10" and changing it to whatever you want.

Declan

---

### Post by wjp.reg on 2007-08-01
> **DeclanMcErlane said:**
> Yeah, I had the same problem a while ago but I sorted it by doing this. Go to terminal and type

```
sudo gedit /boot/grub/menu.lst
```

Scrolling down near the bottom you will see the list of options presented at your GRUB loader. Now remember the number of your XP OS. Scroll upwards again and look for "default 0". Change this to "default (number of XP selection in GRUB Loader)". Then click save. It is also possible to change the timeout if you want a longer/shorter period of time to wait before the OS boots by going to "timeout 10" and changing it to whatever you want.

Declan

And remember that the count starts with ´0´ for the first menu entry, and so on.. :-)

---

### Post by merlinus on 2007-08-01
Not quite.

Numbering for this kind of thing starts at zero, not one.

So after counting down to the windows listing, subtract one from it.

For example, default 4 if windows is the fifth entry.

-merlin

---

### Post by Greensauce on 2007-08-04
ok i'm not sure what I am supposed to change in the menu.lst here is what I have

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6721bde7-df3a-424a-a361-2ae7504b6656 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6721bde7-df3a-424a-a361-2ae7504b6656 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6721bde7-df3a-424a-a361-2ae7504b6656 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6721bde7-df3a-424a-a361-2ae7504b6656 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

and i am trying to set vista as the default OS in grub.

---

### Post by merlinus on 2007-08-04
Is this your entire /boot/grub/menu.lst?

If so, you are missing quite a bit.

If not, then look for a line near the top:

default 0

and change 0 to 4.

-merlin

---

### Post by Greensauce on 2007-08-08
Yea i didn't copy the whole thing i thought everything above that was a commented section. I found the 
```
default 0
```
line and changed it to 4 and with out thinking later that day i restarted the computer and wasn't paying attention to GRUB and it turns out now the default is set to +memtester i think its called. For awhile i thought i massively ****** something up but it was just testing some hardware i guess. But my Vista OS is one more slot down do i change it to 
```
default 5
```

?

Thanks

---

### Post by forestpixie on 2007-08-08
that should be right - but you need to watch when you reboot

---

### Post by EXCiD3 on 2007-08-08
Several times i have set the default to the "Other operating systems:" entry, ;) lol. Most of the options in /boot/grub/menu.lst have descriptions. Best thing to do is read through it, and play with it. ;) Just make sure you don't delete anything important. ;)

---

