---
title: "Where are the Desktop Entries (.desktop files) on Ubuntu 13.04?"
date: 2013-05-18
forum: General Help
---

### Post by gal007 on 2013-05-18
I use to create .desktop files on my Ubuntu 12.04 for my "personalized-apps" to find these applications from the ubuntu dash. I used to store them in /home/gal007/.local/share/applications and they are files like this:

[Desktop Entry]
Name=Eclipse Juno 4.2.1
Terminal=false
Type=Application
StartupNotify=true
Icon=/home/gaby/Development/eclipse/icon.xpm
Exec=/home/gaby/Development/eclipse/eclipse

Now, in Ubuntu 13.04 this directory contains only one file called defaults.list
Where I have to place the .desktop files now?

---

### Post by vasa1 on 2013-05-18
You can still put .desktop files in /home/gal007/.local/share/applications. That it only contains one file right now isn't anything to worry about.

---

### Post by CaptainMark on 2013-05-19
Or the other place for them is /usr/share/applications/

These will be usable system wide by all users, whereas .desktop entries in your home folder will only appear in the dash for your user, 
Use whichever location suits your current needs depending on what you are doing

---

