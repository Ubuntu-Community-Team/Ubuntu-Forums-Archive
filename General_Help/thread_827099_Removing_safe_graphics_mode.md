---
title: "Removing safe graphics mode"
date: 2008-06-12
forum: General Help
---

### Post by Joe of loath on 2008-06-12
hi all;

I'm installing ubuntu on another PC, and as a precaution, I set it to install under 'safe graphics mode'. well, now it's installed and works fine, but I can't seem to set the screen resolution higher than 640x480.

can anyone help?

thanks,
Joe

---

### Post by wolfen69 on 2008-06-12
```
sudo dpkg-reconfigure -phigh xserver-xorg
```then restart x or reboot.

---

### Post by sdennie on 2008-06-12
> **wolfen69 said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```then restart x or reboot.

I don't think this reconfigures the graphics card portion of X in Hardy.  If you can get into X at all, open a terminal and try:

```

gksu displayconfig-gtk

```

---

### Post by Joe of loath on 2008-06-12
> **vor said:**
> I don't think this reconfigures the graphics card portion of X in Hardy.  If you can get into X at all, open a terminal and try:

```

gksu displayconfig-gtk

```

the only option I get is 640x480...

i'll have a look at the boot scripts, but the problem might be the driver. anyone know if the graphics chipset in a dell dimension is supported?

---

### Post by sdennie on 2008-06-12
It should be supported, yes.  Did you click on the "Graphics Card" section of that application and choose a different graphics card?  The other option would be to reboot your machine into recovery mode.  It is an option from the grub menu.  In recovery mode there is an option called xfix that should configure your graphics card properly.

Edit:
The xfix method might be easiest in fact.

---

### Post by simonasambler on 2008-06-12
I have similar probelm with my Geforce go 7300 it found in System-Administration-HW driver my card but what he wasnt able to detected my DISPLAY it means thaht my lcd panel on laptop wasnt recognized. A try everthing, but only working solutions was to manually install drivers /not with apt-get / .

---

