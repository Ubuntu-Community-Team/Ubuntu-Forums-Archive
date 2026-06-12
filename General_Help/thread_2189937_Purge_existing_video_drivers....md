---
title: "Purge existing video drivers...?"
date: 2013-11-24
forum: General Help
---

### Post by RallyDarkstrike on 2013-11-24
Hi guys!

I recently had the video card die in my tinker Linux machine....it was an ATi Radeon 9600 Pro. I swapped in a new video card, which is an Nvidia, but on boot, the machine won't go into X and seems to stop at "checking battery state" while booting...I can get to the command line using Ctrl-Alt-F1 though.

I had read somewhere this could be caused by the video drivers and, considering my machine probably still has ATi drivers installed and now has an Nvidia card, is there any way to purge the ATi drivers and boot into Xubuntu on Xubuntu's "default," "fresh install" drivers so I can then install the Nvidia drivers...? I don't remember exactly what ATi drivers were installed though...

[COLOR=#800080]EDIT - As a note, if I Ctrl-Alt-F1 to the command line and try running "startx", nothing happens and I get the message "xauth - timeout in locking authority file" ...?[/COLOR]

[COLOR=#a52a2a]EDIT 2 - A second note, I've found out I am using the "nouveau" drivers...?[/COLOR]

Thanks for any help! Cheers! :)

---

### Post by Dreamer Fithp Apprentice on 2013-11-24
> **RallyDarkstrike said:**
>  . . . is there any way to purge the ATi drivers and boot into Xubuntu on Xubuntu's "default," "fresh install" drivers so I can then install the Nvidia drivers...?[COLOR=#a52a2a] [COLOR=#a52a2a]. . .[/COLOR] I've found out I am using the "nouveau" drivers.[/COLOR]The "[COLOR=#a52a2a]nouveau"[/COLOR] driver IS the "'default,' 'fresh install' driver" so if you are sure about that, there is no need to purge anything except mafybe to save a small amount of drive space. You can do that after you get the problem solved. Try booting in recovery mode. If it IS some kind of video problem that might get you a working gui environment from which it might be easier to figure out what your problem is.

But> **RallyDarkstrike said:**
> [COLOR=#800080]running "startx", nothing happens and I get the message "xauth - timeout in locking authority file"[/COLOR]sounds more like some kind of permission problem. Did you type in your password? Did it seem to accept it? Possibley there is an error in the file system. Have you tried shuting down with sudo shutdown -h now? If you get the same kind of error that wouldn't be surprising. If so try the hardware shutdown button. I don't mean the power switch. That's a desperation last resort to kill Hal when he has gone beserk and won't listen to you. There is usually a button that will send the equivalent to the shutwown command to the kernel even if your terminal-emulator and tty's aren't working, at least that is what it does ideally, some of the time, unless it is set to do something else, or the god of electrons is p'ed off at you. If you can shut it down cleanly, meaning without resorting to bare bodkin or killing the power, so that the running processes that aren't totally deranged will have warning and do whatever they should do to prepare for the coming power down, and then let it sit quietly for a while just in case there was some kind of overheating somewhere, make sure all the connections (like usb stuff, keyboard, etc.) and any add-on boards (like the graphics card) are firmly seated at both ends if the cable if a cable is involved, then when it powers back up it may start working normally, or it may try to fix a file system error. If it does the latter, if it says something about /tmp or some other directory not being ready and hangs there for a while, try s for skip. When and if it offers you f for fix it do that. If that happens there is a good chance it will fix the problem and reboot and then work. Pay attention to any error messages it throws up and jot them down if need be. If it is just a video driver problem you should be able to get the name of the package you want and install it at the command prompt. But I'm thinking it is more likely a permission problem, which could get a little harrier if one of the above things doesn't work.

---

### Post by Yellow Pasque on 2013-11-24
The only drivers for the Radeon 9600 is the open-source 'radeon' driver (not counting the ancient fglrx/Catalyst 9.3 driver that could only be used with Ubuntu 8.04 or earlier). The various open-source drivers (like radeon and nouveau) don't interfere with each other, so normally, you shouldn't have to do anything special when changing cards. One exception would be if you had a custom xorg.conf, which should be moved out of the way:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If that doesn't work, post/pastebin your /var/log/Xorg.0.log

---

