---
title: "xorg.conf"
date: 2007-12-01
forum: General Help
---

### Post by merlinus on 2007-12-01
Upon fresh alternate cd installs of gutsy, it detects my monitor correctly, and uses the vesa driver for my Matrox P650 card.  I can select a number of screen resolutions including my preferred 1280x1024, and a fine refresh rate.

Unfortunately, however, with the vesa driver I cannot get the monitor to power off after 30 minutes, nor can I activate any special video effects.

I backed up xorg.conf, installed the correct matrox driver, and edited xorg.conf to reflect this. Upon restarting I am greeted with the Matrox Parhelion splash screen, so I know the driver is installed correctly, but it creates garbled displays of text and icons, with words overlapping one another both on menus and in documents.

When I try restoring the backup xorg.conf with vesa driver and restarting, I keep getting the grey configuration screens, and messages to the effect that gutsy cannot deduce my monitor and card. 

I chose the correct monitor (Hitachi CM 751) and screen resolution (1280x1024) from the config menu, but upon bootup it reverts to 800x600 with no other options than 640x480 listed in the dropdown menu.

Help appreciated, as I have already reinstalled gutsy four times just to get back to something useful.

And FWIW, the mtx driver worked perfectly with Feisty.

---

### Post by jken146 on 2007-12-01
A good way to restore the correct settings to xorg.conf safely (sort of) is with the command ```
dpkg-reconfigure xserver-xorg
```

---

### Post by merlinus on 2007-12-01
Good suggestion -- it *should* work, but it does not.  And adding -phigh to that command does not help either.

BTW, it usually needs to be prefaced with sudo.

I can pick whatever settings I want from the screens that come up as a result of entering these commands, but it will boot into 800x600 and not give me any choices for other resolutions than that or 640x480 once in ubuntu.

---

### Post by clubsoda on 2007-12-06
Lack of the higher resolution modes suggests that your graphic memory is not being properly detected.  Have a look through Xorg.0.log for confirmation.
Also, you might try the Parhelia driver from [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at).

---

