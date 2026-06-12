---
title: "KDE keeps rebooting on startup"
date: 2007-04-06
forum: General Help
---

### Post by ndefontenay on 2007-04-06
Good morning,

I was working on an OpenOffice spreadsheet document with Japanese characters when it suddenly crashed.

From that point, my hard disk started writing/reading a lot and KDE became unusable.

I decided to reboot KDE but since then, when it starts, it will reboot shortly after I got the welcome music.

To write this post, I've logged into failsafe mode. I got no kde buttons, no windows bar, nothing.

I've tried to look for some logs but i'm not too sure what logs I should be looking for.

I'm not too sure what to do from now...

---

### Post by ndefontenay on 2007-04-06
I've managed to repair it with envy. I think somehow my nvidia driver got altered in some ways... (So it says...)

But now, I've lost my cool Beryl animations and features.

Beryl is installed.
I got the red diamond in my system tray.
But when I go in the menu "Select Window Manager" and choose "Beryl", I got the screen turning to black for a very short time (I suppose the time it would take to switch). But when I go back to the menu, nothing has changed and the window manager remains KDE.
It seems that somehow Beryl failed and switched to KDE.

I just don't know what's going wrong. Is there a way to get some logs?

---

### Post by ndefontenay on 2007-04-06
Ok.

I was freaking out too much.

I've managed to reconfigure my driver with envy but asked to reconfigure xorg.conf.

my conf file was working just fine before so I took the backup (envy performs a backup first) and replaced the current one with the previous one.

Beryl was not working because the parameters required has been cleaned by the new envy conf.

---

