---
title: "Switch User Black Screen"
date: 2008-03-14
forum: General Help
---

### Post by Literati on 2008-03-14
I know this is a fairly widespread problem, but of the few soltuions I've tried, they don't seem to be working...

First:
"If I can save someone the time of searching it out...

type this in a terminal:

sudo gedit /etc/X11/gdm/gdm.conf

find the line that begins with
#AlwaysRestartServer=false and change it to read
AlwaysRestartServer=true

reboot and you should now be able to log out."

I tried that, but believe it or not, there is NO DATA in my gdm.conf file. So, I'm not exactly sure what to do.
But in any case, yes, pressing log out of switch user will give me a black screen and force me to reboot :(

---

### Post by Literati on 2008-03-14
Anyone able to help?

---

