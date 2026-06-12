---
title: "Add Startup App.....In Blackbox"
date: 2006-11-26
forum: General Help
---

### Post by Hi-Teck on 2006-11-26
I am running an install of ubuntu-server with only Blackbox as my window manager. I want to know how to make the xscreensaver daemon load at startup.

Thanks
Hi-Teck

---

### Post by Ramses de Norre on 2006-11-26
In fluxbox there is a file ~/.fluxbox/startup were you can do this, blackbox has most of these things the same as fluxbox so I'd check the dir with blackbox settings for this.

---

### Post by Hi-Teck on 2006-11-26
No startup file just the menu file under /home/hiteck/.blackbox/

---

### Post by kerry_s on 2006-11-26
If i remember correctly you can create a .xinitrc or .xsession put you startup cpmmands and at the end put exec /usr/bin/blackbox->

For .xinitrc:
#!/bin/sh

your startup command &

exec /usr/bin/blackbox

Not sure if you need the bin/sh, but i think it does need to be executable.

For .xsession it's the same thing but you need to point to it->

sudo (your editor) /usr/share/xsessions/blackbox.desktop

Change> Exec=/usr/bin/blackbox

To your .xsession> Exec=/home/(user)/.xsession

---

