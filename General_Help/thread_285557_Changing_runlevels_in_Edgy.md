---
title: "Changing runlevels in Edgy"
date: 2006-10-27
forum: General Help
---

### Post by Animortis on 2006-10-27
Just got Edgy Eft, but I decided that the best action would be not to use the binary for the Nvidia drivers from the repositories and use the Nvidia beta drivers in the 9000 series. The 8000 series reportedly has a massive security hole in it. However, I cannot figure out how to switch to runlevel 3 so I can install them, since the Nvidia drivers demands I switch to 3 since a running X server interferes with its install process.

Sudo telinit 3 does nothing, does anyone have a workaround?

---

### Post by autocrosser on 2006-10-27
Take a look at the Guide that TSELLIOT has made for Edgy & driver install--there are also several other guides to install the beta drivers (didn't work for me--had to revert to the 8000 series--had two black screens on X start)

---

### Post by tht00 on 2006-10-27
> **Animortis said:**
> Just got Edgy Eft, but I decided that the best action would be not to use the binary for the Nvidia drivers from the repositories and use the Nvidia beta drivers in the 9000 series. The 8000 series reportedly has a massive security hole in it. However, I cannot figure out how to switch to runlevel 3 so I can install them, since the Nvidia drivers demands I switch to 3 since a running X server interferes with its install process.

Sudo telinit 3 does nothing, does anyone have a workaround?

Ubuntu really doesn't use runlevels the traditional way (and thus, I am not familiar with that approach of doing things).

Anyways, Ubuntu does use 'virtual consoles'.  If you hit ctrl+alt+f1 (through f6), you'll get a text based terminal, with ctrl+alt+f7 to bring you back to where you were.

So, what you want to do to install the nvidia driver is this:
-switch to a virtual console: ctrl+alt+f1 
-stop the display manager: sudo /etc/init.d/gdm stop 
-install the driver and make needed changes
-restart gnome: sudo /etc/init.d/gdm start

If all went well, that should bring you back to the login screen with the new driver.

---

