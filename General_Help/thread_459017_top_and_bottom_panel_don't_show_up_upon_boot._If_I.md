---
title: "top and bottom panel don't show up upon boot. If I reload X server, they do!"
date: 2007-05-30
forum: General Help
---

### Post by syxbit on 2007-05-30
this is a real pain
every time i boot up my computer, the panels aren't loaded (top and bottom) so i just have my desktop icons.
if i press CTRL-ALT-DEL, and log in again, they show up.
all i can think of is the 2 recent kernel updates, and me installing a router with WPA2 (so i now have a keychain password)

any ideas?

---

### Post by tgalati4 on 2007-05-30
If you have a lot of stuff in those panels, it could be a bug or configuration error.  Try slimming down the panels and see if they load.  Sometimes moving the icons and applets around will help.

Any errors of insterest in /var/log/Xorg.0.log?

It could also be that during boot some status panels require information to display (like CPU temp) and it takes a minute or so for that information to be available.  In its place, you sometimes get an error message (CPU temp not available!)  These messages won't fit on the panel and they could cause the panel to crash.

When you reload the the xserver, you have now let sufficient time elapse for all of the panel apps to work properly.

Put a sleep 10 somewhere in your bootup script to allow the panel applets to initialize properly.

Or, don't reboot!

---

### Post by syxbit on 2007-05-30
could you explain where to put "sleep 10"
thanks

---

### Post by tgalati4 on 2007-05-31
There are several places that you could put it.  You will have to experiment to see what works.

try:

sudo nano /etc/init.d/bootmisc.sh

add the line:

sleep 10

at the bottom of the file.

---

