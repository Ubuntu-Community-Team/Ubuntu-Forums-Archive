---
title: "Trouble installing entangle"
date: 2014-06-03
forum: General Help
---

### Post by rachel-g41 on 2014-06-03
I can't seem to install entangle (to tether camera) using 13.10.

I tried adding the rep through the terminal then sudo apt-get update then install. It appeared to go ok but couldn't find the program anywhere.I went to synaptic packet manager and tried uninstalling and reinstalling from there, I got an error when I tried to install. 

Program manager, install appeared successful but again I can't find it. Uninstalled from program manager, tried again in synaptic - this time it said installation successful but I still can't find the program anywhere and trying to run 'entangle' from the terminal doesn't work either. 

Any help gratefully received.

---

### Post by 3rdalbum on 2014-06-04
> **rachel-g41 said:**
> I can't seem to install entangle (to tether camera) using 13.10.

I tried adding the rep through the terminal then sudo apt-get update then install. It appeared to go ok but couldn't find the program anywhere.I went to synaptic packet manager and tried uninstalling and reinstalling from there, I got an error when I tried to install. 

Program manager, install appeared successful but again I can't find it. Uninstalled from program manager, tried again in synaptic - this time it said installation successful but I still can't find the program anywhere and trying to run 'entangle' from the terminal doesn't work either. 

Any help gratefully received.

Right-click it in Synaptic and choose Properties. Click the Installed Files tab to see what files were installed and where they were installed to. Anything inside a /bin/ directory, such as /usr/bin/ or /opt/entangle/bin or /usr/local/bin is an executable file.

---

### Post by gordintoronto on 2014-06-04
On my system, entangle is in usr/bin and in Mint's menu under Graphics.

If you are using Ubuntu 13.10, from the dash, type the name.

---

