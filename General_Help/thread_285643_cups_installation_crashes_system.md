---
title: "cups installation crashes system"
date: 2006-10-27
forum: General Help
---

### Post by seaside on 2006-10-27
Hi!
I have a problem with the mentioned above for a while now.
When selecting "cupsys" in Synaptic, or doing a "apt-get install cupsys", my machine crashes when it tries to install the data:
The mouse pointer is no longer visible, the screen freezes and swiching to another tty or restart X by "Ctrl-Alt-Del" is impossible. Only a (hard) reset let me use the computer again.

I thought maybe there is something wrong with whatever data is in the repository, so I downloaded the source code directly from [www.cups.org](www.cups.org) and compiled it myself. But when "make install" reaches a certain point, the screen freezes again. (Copying to Data, or sth like that)

I have little to no idea where to look to solve this problem. The Kernel and System logs don't show events that i can relate to CUPS.


Any help would be appreciated

seaside


p.s:
Ubuntu 6.06
cups sources: 1.2.5, from the repository: 1.2.2
gnome. 2.14.3

---

