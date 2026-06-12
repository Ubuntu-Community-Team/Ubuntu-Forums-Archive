---
title: "Command line install mount problems."
date: 2008-05-23
forum: General Help
---

### Post by anubis2591 on 2008-05-23
Hey all. I've done a command line install off of the Xubuntu 8.04 alt. install disk and built a system off of that. I'm using Fluxbox as a wm and Thunar for a filemanager. Everything has been working fine but for some reason my USB drives won't automount. They mounted just fine with a standard Xbuntu 8.04 install but now nothing. I don't know if I'm missing some package or something but help would be much appreciated. Just ask if you need any more information.

Oh and a weird side note, firefox won't start unless I use sudo. Otherwise it comes up with "Firefox is already running but not responding..." message even when I reboot. I didn't even find firefox as a running process before that message. Not that big of a problem, I was just wondering.

---

### Post by wdaniels on 2008-05-23
Automounting generally relies on hal, dbus and udev, so you need those to start with, but you probably have them already. Usually in Ubuntu it is handled by gnome-volume-manager, but you can use ivman instead to avoid the Gnome dependencies etc. Unfortunately I've never used Xubuntu myself so I don't really know what it normally uses by default.

If you have either ivman or gnome-volume-manager installed already then I'd suggest you have a little dig around in the system log for further clues.

---

### Post by anubis2591 on 2008-05-23
Hey thanks. I didn't have either of them but I went ahead and got ivman. Here's a quick tutorial in case you're looking for the same thing.

To install the ivman package open up the terminal and use apt-get to download and install the package.
```

user@computer: ~$ **sudo apt-get install ivman**

```

Next we'll start ivman. Later we'll make sure it starts up automatically but we need to just make sure it's working first.
```

user@computer: ~$ **sudo /etc/init.d/ivman start**

```

Now that ivman has been started we'll make sure it's working. Plug in a device such as a flash drive. Now, it should appear in the /media directory. Here's what it looked like after I plugged my iPod in.
```

user@computer: ~$ **cd /media**
user@computer: /media$ **ls**
cdrom  cdrom0  floppy  floppy0  IPOD  sdb2

```
As you can see it mounted my IPOD just fine. If you don't see you device you might want to make sure you started ivman as root or check that your USB drive is properly connected.

Now we'll begin to make sure that ivman starts up automatically each startup. This is the prosess if you are using Fluxbox as your window mamager. If you're not see your window manager's documentation for how to add programs to startup. I'll use nano here but you can use any text editor you want.
```

user@computer: /media$ **cd ~/.fluxbox**
user@computer: ~/.fluxbox$ **nano startup**

```
Add the following line
```

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
**/etc/init.d/ivman start &**

```

Now everything should start just fine. Please tell me if I made any mistakes in this tutorial.

---

