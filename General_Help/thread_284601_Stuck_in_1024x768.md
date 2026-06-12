---
title: "Stuck in 1024x768?"
date: 2006-10-25
forum: General Help
---

### Post by bg1256 on 2006-10-25
Just got Ubuntu up and running, and I installed the Nvidia driver that came with Automatix.  

However, I seem to be stuck at this resolution... what can I do to change it?

sorry, I know it's probably been asked before..

-bg

---

### Post by madmetal on 2006-10-25
sudo gedit /etc/X11/xorg.conf
edit the resolutions like that

Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"

but take care to have the ones your vga card and monitor support and then save the changes and exit..

---

### Post by Shay Stephens on 2006-10-25
And just to add, you have to log out and back on, or reboot for the change to be usable.

---

### Post by bg1256 on 2006-10-25
alright cool... but the nvidia driver in automatix will do the trick?

---

### Post by boris357 on 2006-10-25
Also, If you are running Ubuntu with the gnome desktop you can click System on the display bar. Next click preferences then scroll down to Screen Resolution. Open it and select the resolution you wish.

Happy surfing.
Larry

---

### Post by bg1256 on 2006-10-25
Yes, but said title is highest available resulotion, atm.

I'm still working on it! :P


Edit: finally got 1280x1024.

Thanks to all!

---

