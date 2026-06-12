---
title: "Cant perform a Live boot"
date: 2005-10-23
forum: General Help
---

### Post by lardiop on 2005-10-23
Hi all,

I just finished download the x64 live CD of Breezy Badger. Everything works fine in the Live Cd boot process until the very end when i get the following blue screen error:

"Failed to start the X Server (Your graphical interface) It is likely that it is not setup correctly. Would you like to view the x server output to diagnose the problem?"

And thats it, Ubuntu just says no and doesnt do anything else. Ideas? Thoughts?

System is an AMD Athlon X2 4200+, 1GB DDR400, Radeon x850xt

---

### Post by aysiu on 2005-10-23
I'm no expert on this x server stuff, but have you tried typing ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by lardiop on 2005-10-23
[QUOTE=aysiu]I'm no expert on this x server stuff, but have you tried typing ```
sudo dpkg-reconfigure xserver-xorg
```?[/QUOTE]
There is no terminal or prompt to enter it at

---

### Post by aysiu on 2005-10-23
At the first boot screen, press F5. You should get something that looks like [this](http://i22.photobucket.com/albums/b337/psychocats/04973d58.png). Those are boot options. You can try different things out. For example, you can try typing ```
boot vga=791
``` and see if things change.

---

