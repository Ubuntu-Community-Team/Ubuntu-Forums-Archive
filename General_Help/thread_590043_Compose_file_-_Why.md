---
title: "Compose file - Why?"
date: 2007-10-24
forum: General Help
---

### Post by lundbech on 2007-10-24
Been fooling around a bit trying to find out why the greek polytonic (ancient greek) keyboard layout practically doesnt work at all. 

My locale IS en_US.UTF-8, (although I use the danish keyboard-layout (tryin to avoid the danish parts of the system, because the translations really suck)) so I figured that I should edit this file:

/usr/share/X11/locale/en_US.UTF-8/Compose 

to try to find out whats what, but none of it had any effect. So I deleted the whole greek polytonic part af the file, restarted X, and behold the few greek accents that worked before still work.

Does that mean that:

/usr/share/X11/locale/en_US.UTF-8/Compose  

is not the right file? What is then? Where?

Please help.

/phl

---

### Post by lundbech on 2007-11-01
For the record:

Seems the greek polytonic keyboard is simply broken in Ubuntu. Switched til Kubuntu and all problems are solved. (although you might want to apply this: [http://www.jw-stumpel.nl/stestu.html#T6.5.3](http://www.jw-stumpel.nl/stestu.html#T6.5.3))

/lundbech

---

