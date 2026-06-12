---
title: "Ubuntu doesnt start any more!!! HELP"
date: 2007-02-27
forum: General Help
---

### Post by Tag_yer_dead on 2007-02-27
Hi everyone
Please help, Ubuntu has been working fine for me, im getting good with using it BUT...... i booted it today, and now it wont boot any more.  It makes it to about 1/4 way on the start up bar and then the ubuntu logo goes black and weight (makes me think its a driver issue?)  How can i fix this?

Computer: Asus Pentium 4 3.88 Ghz
ati radeon x850xt
4 gb ram
500 gb hard drive

Please help, thanks.

---

### Post by taurus on 2007-02-27
Boot into recovery mode and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```
Use **vesa** as the driver for your graphic card.

---

### Post by Tag_yer_dead on 2007-02-27
i can boot in recovery mode by selecting that from the partition list right?

and do i have to use vesa, radeon has been working fine

---

### Post by lamego on 2007-02-27
It's not the partition list, it's the grub menu that you get just after powering on your system...
There should be a label with "Recovery"

---

### Post by taurus on 2007-02-27
You choose the recovery mode from GRUB menu.  When you turn your computer on, you will see a GRUB menu (after all the self checks from the BIOS) and if you don't, you have to press Esc when you see the GRUB screen with time counting down, 3 seconds.  

You can choose radeon again if you want and if that doesn't work, then try vesa.

---

### Post by tomzx on 2007-02-27
you could try my miracle receipt, it has always worked for me when I couldn't get  past the black screen.

Boot in recovery mode (the second one) when in console type

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo install xorg-driver-fglrx

(note that you'll need your live cd in order to get those installed from it)

you'll need to configure your radeon, so type

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Good luck with that!

---

