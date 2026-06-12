---
title: "gnomes volume manager wont start"
date: 2008-03-23
forum: General Help
---

### Post by krispa on 2008-03-23
So I just started ubuntu (7.10) and now I cant open "gnome-volume-control". When I double click on the volume button up in systry (which is gnome-volume-control)  it says "Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)".

And I've tried rebooting. :confused: 

Anyone know a solution?

---

### Post by tgilber1 on 2008-03-23
Either you do not have the gnome-media package installed or the gnome-volume-control file was accidentally deleted.  In any event, try the following:


[LIST=1]
[*]Open a terminal window and type:  dpkg -l gnome media
       should get a response like the following: 
       ii  gnome-media    2.20.1-0ubuntu GNOME media utilities
       ii = installed
       rc or pn = means the package has to be re-installed    
[*]If the package is installed, try reinstalling:  sudo apt-get install --reinstall gnome-media
[*]if it is not installed, then install:  sudo apt-get install gnome-media
[/LIST]

---

### Post by krispa on 2008-03-23
Thank you, that worked. I was making my install as minimal as posible, and deleted "gnome-media" thinking that the only thing in the package was the sound recorder.

---

