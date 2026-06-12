---
title: "wine-pthread locking up wine"
date: 2006-12-21
forum: General Help
---

### Post by Kimm on 2006-12-21
Sometimes when I close a program running in wine, wine will leave a process behind (wine-pthread), that will make me unable to run any software with wine untill after I reboot...

wine-pthread is, as it seems, indistructable, I am simply completely unable to kill the process. I have tried:

killall wine-pthread
and: killall -9 wine-pthread -s SIGKILL

gnome-system-monitor tells me the process is uninteruptable, why?

does anyone else experiance this? is there a fix?

It's pretty annoying when the last thing I have to do before shutting the computer down is check if a (home written) windows program will work or not.

---

