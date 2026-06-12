---
title: "After rebooting, keyboard configuration resets"
date: 2014-11-18
forum: General Help
---

### Post by canhoto on 2014-11-18
Hi.


I've Ubuntustudio 14.04 installed on my Macbook. I've installed Cinnamon besides the XFCE default DE that comes with Ubuntustudio.

I'm having some problems with keyboard layouts, especially in the default XFCE environment.To make an "alt" sign nothing happens when I try to change layouts within the "Settings" app.

To have some success I have to make ```
sudo dpkg-reconfigure keyboard-configuration


```

And then choose "Macintosh"->"Portuguese"->(choose a key for "AltGr")->(choose a "compose" key)->(choose to use Ctrl-Alt-Backspace). Then everything works fine.

Then, when I reboot, it doesn't work anympore, and I have to do everythink again.

Any help?

---

