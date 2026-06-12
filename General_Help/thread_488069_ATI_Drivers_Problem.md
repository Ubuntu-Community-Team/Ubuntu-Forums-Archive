---
title: "ATI Drivers Problem"
date: 2007-06-29
forum: General Help
---

### Post by Salazar420 on 2007-06-29
So, I've tried this: [http://doc.gwos.org/index.php/TVout_for_legacy_ATI_cards_using_GATOS](http://doc.gwos.org/index.php/TVout_for_legacy_ATI_cards_using_GATOS) tutorial several times on several different installations of Ubuntu, and each time all seems to go smooth, until the time to make comes:
> 
xenouser@matthew-desktop:~/atidrivers/xf86-video-ati-6.5.8.0$ make
make: *** No targets specified and no makefile found.  Stop.

It happens "every" time on "every" installation, all of which were Feisty Fawn. Next comes "sudo make install" command.
> 
xenouser@matthew-desktop:~/atidrivers/xf86-video-ati-6.5.8.0$ sudo make install
make: *** No rule to make target `install'.  Stop.

...only to yield the very same result. It's unfortunate because I feel like this could be the only barrier standing before me and the final success of tv-out with my Radeon 9250 video card. If anyone could lend some assistance I'd greatly appreciate it.  --- Salazar420

---

### Post by tronica on 2007-06-29
did you do a ./configure before make. Also try doing sudo make and sudo make install

---

### Post by Salazar420 on 2007-06-29
Tried ./configure -- performed the expected actions. Tried make, sudo make and sudo make install -- all of which yielded the same, disconcerting results as before.

---

