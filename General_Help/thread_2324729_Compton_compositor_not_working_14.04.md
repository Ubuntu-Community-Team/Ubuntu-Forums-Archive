---
title: "Compton compositor not working: 14.04"
date: 2016-05-16
forum: General Help
---

### Post by Osmodivs on 2016-05-16
Hello.
I have** Lubuntu 14.04 64 bits** with a** R9 380 GPU** with propietary drivers (**15.302**). I had in my repositories *ppa:richardgv/compton* and *ppa:kelleyk/compton* right now.
I can't make Compton compositor work in my machine, I have followed several tutorials from the web with no luck. I have edited:
~/.config/lxsession/Lubuntu/autostart
~/.config/openbox/autostart
/etc/xdg/lxsession/Lubuntu/autostart
and added a simple @compton -c -r 16 -l -24 -t -12 -G -b wich looks fine for me, logout and login and no special effects for me. I then deleted all those lines from the autostart files (wich where empty before adding anything) and used Preferences>LXSession for default apps and added compton in compositer manager empty box, reloaded, and now clicking in the menu icon does nothing, the right mouse button does not work, some icons in my panel do nothing when clicked, Lubuntu just got messed up trying to make Compton compositor work for me, I do want special effects in my DE and I don't want to reinstall. Is there a way to reset all stuff and make Compton work?


Edit: I deleted compton from Synaptic and now menus work. But I still want Compton

---

