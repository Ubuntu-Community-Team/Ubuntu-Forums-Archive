---
title: "How to autologin in Xubuntu?"
date: 2006-07-22
forum: General Help
---

### Post by Dusk2k2 on 2006-07-22
I've just installed Xubuntu on my parents computer.  Needed to because Ubuntu was running a little slow.

But how do I make Xubuntu autologin?  My parents won't be able to bother with logging in each time, and I want to make their linux experience as easy as possible.  Any help would be greatly appreciated.

---

### Post by aysiu on 2006-07-22
Alt-F2 ```
gksudo gdmsetup
```

---

### Post by euchrid on 2007-11-25
I found that the above command would not work for me because I had KDM installed. Even when I chose GDM as the default display manager, I could not run gdmsetup. I found that uninstalling KDM solved this issue; KDM is not necessary to run KDE programs. Obviously, I am running Xubuntu, not KDE or GNOME.

You can also achieve this by choosing Settings>Login Window from the Main/Applications Menu and choose XFCE as your default session (or whatever you prefer), and then go the Security tab and click 'enable automatic login' for the appropriate user. If you don't know what you're doing, don't touch anything else.

PLEASE NOTE: The Login Window will NOT appear on the menu in XFCE or GNOME if you have KDM installed. At least, it wouldn't for me. KDM kind of takes over. Remove it using Synaptic or apt-get unless you need it for a specific theme (unlikely if you are running Xubuntu). You do NOT need to uninstall KDE, just KDM!

---

