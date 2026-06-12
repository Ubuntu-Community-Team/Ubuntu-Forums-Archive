---
title: "On what data and time was my Ubuntu installed?"
date: 2007-03-24
forum: General Help
---

### Post by lawina on 2007-03-24
On what data and time was my Ubuntu installed in my machine?
The 'last' command is inaccurate for me.

---

### Post by superatrain on 2007-03-25
One simple technique is look at a file which probably hasn't been touched since you've installed your system.

Look around for stuff that contains hostname, or packages that haven't been upgraded, or the original kernel in /boot/.

for example, /etc/svgalib on the computer I'm on now (Gentoo)  hasn't been touched since it was installed.

---

