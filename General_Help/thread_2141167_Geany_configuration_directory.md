---
title: "Geany: configuration directory"
date: 2013-05-01
forum: General Help
---

### Post by Ctulhu on 2013-05-01
I just installed Kubuntu 13.04 normally from a DVD. Then, using Synaptics Package Manager, I installed geany and its plugins, which I have been using for years now). However, now when I start geany (either from the 'start menu' or from the console, a window pops up saying

# -----------------------
Configuration directory could not be created (Permission denied).
There could be some problems using Geany without a configuration directory.
Start Geany anyway?
# -----------------------

However, geany's configuration directory is where it's supposed to be (according to the geany online manual): /home/Ctulhu/.config/geany/

What can I do to get rid of that window and use geany normally?
C

---

### Post by mdavies5 on 2013-05-02
Check the permissions of [COLOR=#000000] /home/Ctulhu/.config/geany/ and all it's subfolders and files. Make sure you have permission to read/write to files and create/delete files in folders. This problem occurs if you copied any of your Home folder from another installation. The permissions are immediately set to Root because user 'ctulho' is not recognised on the new system, even if you logged on with the same name.[/COLOR]

---

### Post by Ctulhu on 2013-05-02
TBH, I can't imagine that that's the problem because it was a completely fresh install, w/ formatting all partitions etc., but one never knows so I will of course try it, thx!

---

### Post by Ctulhu on 2013-05-03
You were right, it was the permissions issue, the whole folder was owned by root and I changed that; now it works, thanks a lot. Non idea how this could have happened with the normal kind of installation, I gotta say, but who cares now :-)

(And if there was a menu/button or something in Thread Tools or Go Advanced, I would even mark this as SOLVED ...)

---

