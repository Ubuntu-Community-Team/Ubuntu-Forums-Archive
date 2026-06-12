---
title: "Ubuntu update broke everything?"
date: 2015-02-01
forum: General Help
---

### Post by garydebergerac on 2015-02-01
So, I got the little notification that there was some updates, including Ubuntu base, so I started the download.  I was doing some other stuff, and to be honest I didn't ever see anything pop up in terms of a progress or anything like that.  I also installed some other stuff (inkscape, virtualbox) and when I went to reboot, the shutdown button (top menu) asked me for my password, which I thought was odd.  Actually, before this happened I had noticed that Inkscape had disappeared-  I was using it and then shut it down, and when I went back to re-open it, the search box didn't return it.

Anyway, i just hit the button on my machine, the shutdown dialog popped up and I then went into Windows to do some other stuff.  When I rebooted back into Ubuntu, my file menu (left), top menu (sorry I don't know these names yet, new) had disappeared.  When I started the Software center, I got a Synapitcs package manager request for my password, as though software manager had been replaced by synaptics manager.  None of my windows have toolbars, and Unity Tweak tool doesn't seem to be installed anymore either.  A couple of things, like Kodi and Virtualbox and Cairo, still show up in the Application Menu (good thing Cairo is still working!), but that seems to be about it.

I literally just installed this yesterday, or at least for what I thought was the last time with my Windows boot and everything working.  This was pretty much the first update, although maybe installing the other stuff installing at the same time messed something up?  I had honestly forgotten it was updating, so maybe it wasn't finished?  No idea, but completely broken now, that is for sure.  Any suggestions, besides re-installing?

---

### Post by mooreted on 2015-02-01
Maybe you rebooted while updates were still installing and some of them didn't complete. Open a terminal and do:

sudo apt-get update
sudo apt-get upgrade

You may need to set Unity and Compiz back to defaults:

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Also, are you sure you booted into Ubuntu (Unity) and not some other window manager? If you log out, there is a little round icon next to your name. If you click it, it allows you to boot into other window or desktop managers.

---

### Post by garydebergerac on 2015-02-01
You know, I started to realize that maybe "broke everything" was inaccurate, and maybe broke unity would be more appropriate.

Then I tried to find Terminal.  Nope, broke everything!  :)  No terminal, and no logout buttons either.  Literally just the desktop and cairo dock, so if it's not accessible from there, it's not accessible. Ctrl+Alt+T doesn't do anything either.

---

### Post by oldfred on 2015-02-01
Can you then from grub menu boot in recovery mode. And then enable network and in terminal run updates/repairs?

---

### Post by Erik1984 on 2015-02-01
You can always go to TTY (CTRL + ALT + F1) to enter commands if the graphical terminal is not working anymore. (CTRL + ALT + F7 should bring back the graphical desktop)

---

### Post by garydebergerac on 2015-02-01
TTY not working either, and network-manager can't find any devices when enabling networking from the recovery menu.

---

### Post by mJayk on 2015-02-01
> **garydebergerac said:**
> TTY not working either, and network-manager can't find any devices when enabling networking from the recovery menu.


If tty is broken then you are pretty buggered, just reinstall wont take more than 15 mins and then restore you backups.

---

### Post by garydebergerac on 2015-02-01
yeah, 15 minutes was dreaming, but I am back and did all the upgrading before everything else, so hopefully nothing like this will happen again.  Thanks for your replies

---

### Post by mooreted on 2015-02-01
Good luck. Fortunately, Ubuntu is pretty darn stable. Anything can break, however.

---

