---
title: "Disable mouse in tty?"
date: 2015-01-15
forum: General Help
---

### Post by ben132 on 2015-01-15
I use an Asus EeePC netbook with Xubuntu 14.04. I've disabled tap-to-click in X so I don't accidentally click while typing just by brushing the touchpad. If I use ctrl-alt-(f1-f6) to access the ttys, though, the mouse is active and tap-to-click is on. I've searched around for how to disable mouse support at the tty, but haven't found anything useful - I don't even know the name of the service that provides it. How can I keep the trackpad working in X but disable it entirely at the ttys and make them text-only?

---

### Post by ben132 on 2015-01-16
Well, I've figured it out. The mouse-in-tty service is gpm and can be stopped with
[FONT=lucida console]sudo service gpm stop[/FONT]
and prevented from launching at startup by creating a file at /etc/init/gpm.override containing the word 'manual'.

---

