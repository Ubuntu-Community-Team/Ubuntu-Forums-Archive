---
title: "Google Earth stop working on ubuntu 12.04"
date: 2013-05-24
forum: General Help
---

### Post by offir on 2013-05-24
I installed Google Earth 7 on a Ubuntu 12.04
Everything worked great:p

Before four or five days
Google Earth has stopped working correctly:(

The only way to run Google Earth is after restarting the computer

If I close the Google Earth and a few minutes and later i  want to run the software again
The software does not work , Google Earth is not launch
you See a few seconds the screen opening Google Earth with Google logo
And that is closed

my system is 32 bit

---

### Post by Impavidus on 2013-05-24
Try starting it from a terminal:```
google-earth
```(I think. It works on my machine)
It may give you a useful error message.

---

### Post by rewyllys on 2013-05-24
What solved my problems with using *Google Earth* in Linux was installing, from the Linux Mint Software Center, the utility named "googleearth-package".  Its purpose is stated as: "Utility to automatically build a debian package of google earth."  Installing it resulted in *Google Earth* being listed in the LM Menu, under "Internet".

I assume that this package is also available from the Ubuntu Software Manager.

---

### Post by offir on 2013-05-24
> **Impavidus said:**
> Try starting it from a terminal:```
google-earth
```(I think. It works on my machine)
It may give you a useful error message.

I started it through the terminal

This is what I got





Failed to load "/opt/google/earth/free/libmeasure.so" because "/opt/google/earth/free/libmeasure.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libwebbrowser.so" because "/opt/google/earth/free/libwebbrowser.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libgps.so" because "/opt/google/earth/free/libgps.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libbasicingest.so" because "/opt/google/earth/free/libbasicingest.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libsearchmodule.so" because "/opt/google/earth/free/libsearchmodule.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libinput_plugin.so" because "/opt/google/earth/free/libinput_plugin.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libflightsim.so" because "/opt/google/earth/free/libflightsim.so: cannot open shared object file: Too many open files"
Failed to load "/opt/google/earth/free/libviewsync.so" because "/opt/google/earth/free/libviewsync.so: cannot open shared object file: Too many open files"

---

### Post by piperbarb on 2013-05-24
I had the same problem.  I reinstalled google earth from the Synaptic package installer and now it's fine.

---

### Post by offir on 2013-05-25
I have no problem to install the software again
The question why this is happening in the first place

And how to prevent it happening again
In short find out what the problem

---

### Post by offir on 2013-05-25
anybody ?

---

### Post by nicklcanada on 2013-08-05
You can launch application with: 

gksudo -k -u root /opt/google/earth/free/google-earth %f

or 

1. Edit sudoers file:

gksudo gedit /etc/sudoers

-add this line:

yourusername ALL= NOPASSWD: /path/to/the/command

remplace 
/path/to/the/command 
with 
/opt/google/earth/free/google-earth



2. Run your app in launcher or terminal with:

sudo google-earth

---

