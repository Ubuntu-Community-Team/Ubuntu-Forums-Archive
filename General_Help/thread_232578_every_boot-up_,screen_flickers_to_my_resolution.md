---
title: "every boot-up ,screen flickers to my resolution"
date: 2006-08-08
forum: General Help
---

### Post by quedigg on 2006-08-08
Hi fellows,
i've switched my resolution 1024x768 ,however ,everytime i boot , it uses the resolution i got from the system installation ,then flickers to my recent resolution .it's running smoothly, but is there any way to make this resolution permanent from the beginning (from the point x-server starts)?
i've also had a look on xorg.conf ,at screen section(s) ,appear too many configurations with varius depth values.

many thanks in advance .

Q.

---

### Post by Anduu on 2006-08-08
Technically X starts at the login screen(well the instant before actually...).....

Are you referring to the resolution change when the login screen pops up?

It is possible to change the resolution of the bootup messages(the usplash)however you will probably still get a flicker as the login screen pops up...I do.

Changing the usplash resolution requires editing grubs boot menu...

In terminal type 

```
sudo gedit /boot/grub/menu.lst
```

Find the section for the kernel you boot...it will look something like this:

```
title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda2 ro quiet splash [COLOR="Red"]vga=792[/COLOR]
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot
```

See the red highlighted entry...this will change your usplash resolution to 1024x768

---

### Post by quedigg on 2006-08-09
thanks ,
but it's not about the boot screen ,it's as you tell , from the login screen ,to the desktop ,it's flickers the resolution here.

---

### Post by Mau on 2006-08-09
My bet is that you have one screen resolution set as the default for the computer, and then a different one for your account.  If you go to System -> Prefs -> Screen Resolution, is "Make default for this computer only" set?

---

