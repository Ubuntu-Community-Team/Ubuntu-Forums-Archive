---
title: "Shutdown and Restart"
date: 2006-11-22
forum: General Help
---

### Post by pastorjay on 2006-11-22
Is there a way to make a shutdown and restart icon fro my startbar?  I have done it in windows, and am wondering if it can be odne in ubuntu as well!

---

### Post by o_fortuna on 2006-11-22
I'm not sure if there's a "cool people" easy way to do it, but you could just make a couple of shell scripts and put links on the taskbar. I guess one for shutdown would be
```
#/bin/sh
sudo shutdown -h now
```
and for restart would be 
```
#/bin/sh
sudo shutdown -r now
```
Although those lines might not be exactly correct, but they shouldn't cause problems I guess (well, it shouldn't, anyway).

Then you would save the files (like the first as shutdown.sh and the second as restart.sh) and make links and drag them to the taskbar. This should work.

These two scripts (if you could call them that) are provided as is and with the hope that they will be useful, but without warranty of any kind. Just so you know. And I haven't even tried them... sorry.

OH! You need to make the script (not the link) executable (right click, Properties, Permissions, and check allow execution).

---

