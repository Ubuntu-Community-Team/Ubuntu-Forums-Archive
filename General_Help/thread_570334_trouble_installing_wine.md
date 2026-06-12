---
title: "trouble installing wine"
date: 2007-10-08
forum: General Help
---

### Post by Placified on 2007-10-08
I've looked and looked but somehow I can't seem to make this work.  I'm running ubuntu and when I install wine everything seems to go ok but it wont creat the directories ./wine and what not.  I have tried many different methods and none have worked thus far.  the program installs and the shortcuts are there but I have zero functionality.  if anyone else has had this problem please let me know how you fixed it, thank you.

---

### Post by ronald.higgins on 2007-10-08
Open up a terminal (should place you in your home directory) and run:

winecfg [hit enter]

This will set up the relevant paths and files :)

Then to run you application first copy the file to /home/$yourhome/.wine/drive_c/Program Files/$yourdir and to actually run it type "wine /home/$yourhome/.wine/drive_c/Program Files/$yourdir/executable"

---

### Post by Placified on 2007-10-08
Thank you! I cant believe I overlooked something that simple.  it's people like you that answer the "stupid" questions for the noobs like me that keep this stuff alive thanks again

---

### Post by ronald.higgins on 2007-10-08
Cool beans buddy :)

---

