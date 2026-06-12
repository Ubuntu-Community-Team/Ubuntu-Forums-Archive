---
title: "Libreoffice Writer shotcut doesn't work"
date: 2012-12-23
forum: General Help
---

### Post by arrjayjee on 2012-12-23
I'm trying to make a shortcut for Libreoffice Writer but it's not working. I get an error saying:

> This link cannot be used, because its target "../../lib/libreoffice/share/xdg/writer.desktop" doesn't exist.

I've taken screenshots of the problem here:

[http://imgur.com/a/gJOPM](http://imgur.com/a/gJOPM)

I'm running Libreoffice version 3.5.4.2 on Ubuntu 12.04

Can anybody help?

---

### Post by dreamquartz on 2012-12-23
which version on what platform are you using?  Dream

---

### Post by arrjayjee on 2012-12-23
LibreOffice version is 3.5.4.2

I'm running Ubuntu 12.04

---

### Post by dreamquartz on 2012-12-23
Did you try looking for it? Easiest way of doing that is via *sudo nautilus* in Terminal and goto File System to start searching.
Did you try the same with another program within the Suite? If not, try to duplicate the issue with an other like Calc.
Is the icon available under Dash Home -> Installed? If so, you can try to move it to the Desktop via L mouse click and drag.
It will not be the one that you can do anything with it as this point, but you can look up the Properties. You can then see where it is referring to.

When I want to get the Suite icon to the Desktop, after a new install, I do the following:

[LIST=1]
[*]Drag icon to Desktop from Dash Home ->  Installed
[*]                      Open Terminal
[*]Enter *gnome-desktop-item-edit ~/Desktop/ --create-new* in Terminal
[*]Copy the Command (via Properties -> Basic Tab -> Command) into Launcher
[*]Change icon by clicking on it (I use the one under /usr/share/icons/hicolor/48x48/apps)
[/LIST]
Maybe this helps
Dream

---

