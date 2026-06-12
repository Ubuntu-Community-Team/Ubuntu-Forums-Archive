---
title: "Display problem"
date: 2007-08-27
forum: General Help
---

### Post by lazysloth on 2007-08-27
when i boot up ubuntu there is this message that says 
video mode not supported
i then press ctr+alt+f2 and then the error message goes away and then the display is normal.

the problem is i dont want to keep pressing ctr+alt+f2 everytime to get the right display each time i boot up ubuntu... is there a way to solve this?

thx

---

### Post by gobbles414 on 2007-08-27
Greetings lazysloth,

Have you looked in *system --> administration --> restricted drivers manager* to see if there is an additional video driver available for your system? If there is another driver available but it fails to install from the restricted drivers manager, you may be able to force the driver to download by going *system --> preferences --> desktop effects*.

---

### Post by lazysloth on 2007-08-29
i get this.. i dont know what this means.. 
"Your hardware does not need any restricted drivers."

---

### Post by gobbles414 on 2007-08-29
lazysloth,

My guess is that your system uses 100% open source drivers. Restricted drivers are what is known as "closed source". Anyway, another question... Are you using more than one computer monitor?

---

### Post by lazysloth on 2007-08-29
only one monitor...
maybe this might help u?
after typing "lspci" in terminal i got
> 
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
here is my xorg.conf file... iono if that will help solve the problem..
[http://hostfil.es/file/3963/xorg-lookatmyconf.html]("http://hostfil.es/file/3963/xorg-lookatmyconf.html")

again, the problem is when i boot into ubuntu... which works fine and all..i even got beryl working :) Its just that once i go to the grub and select Ubuntu... it says Video Mode Not Supported, i then can bypass this error by pressing Alt+f2(i found that somewhere... and it works  to land me on the login screen.
thx for the help so far...

---

### Post by rsambuca on 2007-08-29
It sounds like the video setting in your boot options.  Change the setting in your /boot/grub/menu.lst.

---

### Post by lazysloth on 2007-08-30
title Microsoft Windows XP Professional
root (hd0,1)
makeactive
chainloader +1
boot

title		Ubuntu
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b34dc24a-ea19-4517-a7b3-d99e0bf052e9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

i used wubi then i moved it to a real partition...
then i took off the other kernals off the menu.lst

---

### Post by lazysloth on 2007-08-30
default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 2.6.20-16
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/sda6 ro single
initrd /boot/initrd.img-2.6.20-16-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot

i edited it to this...

---

### Post by lazysloth on 2007-08-31
default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 2.6.20-16
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
boot

title		Ubuntu 2.6.20-16 no splash
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda6 ro quiet
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
boot

title		Ubuntu 2.6.22-10
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-10-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet
savedefault
boot


title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-16-generic root=/dev/sda6 ro single
initrd /boot/initrd.img-2.6.20-16-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot

woot i found the problem.. the splash screen was the problem.. i added a no spash screen option on the menu.lst and it didnt get that annoying "video not supported message"..
also i got a new kernal installed while i was messing around with the menu.lst...

i still want the splash screen... does anyone know why when i jump into the splash screen the video mode is not supported?  even tho all that scrolling text is cool when you want to figure out a problem... it doesnt look very good as the splash screen :).

---

### Post by lazysloth on 2007-09-06
problem solved.
i stopped being cheap and bought some blank cds and installed the ubuntu iso and burned it to a cd and used that instead and now i have a splash screen...

The problem was i was using an alternate iso for ubuntu when i installed ubuntu through wubi...

i suggest if u use wubi and u want to move it to real partitions that u download the ubuntu iso and burn that to an iso and install that to a real partitions because the alternate iso that comes with wubi messes up my splash screen..:guitar:

---

