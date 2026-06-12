---
title: "ATi Drivers and Dual Screen Set-up"
date: 2005-03-20
forum: General Help
---

### Post by Leebobs on 2005-03-20
I have an ATi 9800 Pro, I installed the drivers as directed by Wiki and then did an apt-get for fglrx-control, which seemed to install ok.

Now I'm trying to configure my dual screen displays and I have absolutely no idea how to do it!!! Can anyone help?  :( 

Thanks

Leebobs

NB: Screen Resolution is no longer working :-k 

Ditching M$ and Learning Linux is hard  ](*,)

---

### Post by emuman on 2005-03-21
Dual Screen with TV-Out works for me with the lastest Ati closed source drivers 8.10.19. You are using 8.8.25 from ubuntu I guess.
First save your existing '/etc/X11/xorg.conf'. Start 'fglrxconfig' as root. In the screen 'FireGL Screen Layout' it'll ask you, if you wan't dual screen. Select 'Big Desktop' (one desktop) or 'Dual Head' (two desktops). On one of the next screens you can choose the connection type (VGA, DVI, TV) and resolution for your screen. Go ahead and save the configuration. Compare your backup xorg.conf with the new generated and check the setting for mouse, keyboard and screen resolution. If everything is okay restart X.

---

### Post by bobmitch on 2005-03-21
NB.  When asked about external agpgart in the 'wizard' - answer the opposite to the default.  This is a known bug.

---

### Post by Leszek Tarkowski on 2005-03-21
Hi. I got dual head for purpose of watching movies on tv-out configured. I used ifo on 
[Gentoo-Howtos](http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV). I still have one problem. I don't want Gnome on second display. I would prefer some "light" manager, or even xterm only. How to do this?

Also maybe there is possibility (sure it is) to have session choice in GDM, to select dual-head versus single (different xorg.conf)?

---

### Post by Leszek Tarkowski on 2005-03-24
Now i knew what i want :)
I want to choose in gdm if i want single-head, dual-head etc. by forcing X to use different xorg.conf files. I have messed with [server] section in gdm.conf but without spectacular succes. Maybe ubuntu (as a distro with already great support for notebooks) will solve that (as a sort of patch for gmd or something).

Please - this is quite important for laptop users - possibility to use external screen is mandatory.

---

