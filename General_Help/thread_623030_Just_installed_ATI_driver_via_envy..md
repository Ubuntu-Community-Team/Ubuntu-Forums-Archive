---
title: "Just installed ATI driver via envy."
date: 2007-11-25
forum: General Help
---

### Post by SSB on 2007-11-25
This has always worked before.. but after enabling the restricted one that gutsy tries to nab, compiz stopped working. So I grabbed Envy. It worked, but now when I try to log in, I'm just presented with a white screen. I can move my mouse around, and restarting X gives me a brief view of my desktop before returning to the login screen.. but I am lost. This is on a completely fresh install.

Help?

---

### Post by SSB on 2007-11-25
Sorry to bump, but I'd hate to have to reinstall ANOTHER TIME. I'd at least like to know how to install the open radeon driver instead.

---

### Post by SSB on 2007-11-26
last bump before i give up hope.

---

### Post by NT4usB on 2007-11-26
I don't know anything about this compiz except lots of folks having trouble with it.
Don't even know if this will work with compiz installed but you can try it...

Ctrl+Alt+F1. login and type:```
sudo envy
``` then type it again with whatever it prompts you to type... there's something else belongs on the line but I can't remember what it is.
Select the option to completely remove the ATi stuff.
Then choose the option to install...

-or-

Ctrl+Alt+F1
login, then type:```
sudo dpkg-reconfigure -phigh xserver-xorg
```Restart.
If that doesn't work, do it again but leave out the -phigh
It will take you through a bunch of configuration. When you get to the video driver, choose vesa.
Then you'll have a desktop to look at.

ed: or if you know how, edit your xorg.conf and change the driver to radeon (or vesa, or?).

---

### Post by aldenhg on 2007-11-26
You need to read any of the hundreds of guides there are to get Compiz working on an ATi card. Here's a good starting point:
[http://ubuntuforums.org/showthread.php?t=591445&highlight=compiz+ati](http://ubuntuforums.org/showthread.php?t=591445&highlight=compiz+ati)

---

