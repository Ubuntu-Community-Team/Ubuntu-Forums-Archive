---
title: "Setting the default application"
date: 2013-09-01
forum: General Help
---

### Post by sideburns on 2013-09-01
Right now, my sister's trying to install a Windows app that she needs for school on her Xubuntu box.  Simply clicking on the file opens archive manager, which fails, of course.  We have to right-click on the file and select opening it with Wine.  And, as the installer's been giving us trouble, we've had to do this more than once.  How do we tell Ubuntu that we want all .exe files to be opened by Wine by default?  It's trivial under Xfce and Fedora 19 (Right-click, select Open with Other Application and check the box making your choice the default) but that doesn't work under Ubuntu.

---

### Post by fadhil-hakadir on 2013-09-01
hi,

what release is she using?  i'm on xubuntu 12.04, and the trivial step you just mentioned worked fine for me. 

similar to the first answer here:

[http://askubuntu.com/questions/272134/default-application-to-open-text-file-in-thunar-under-awesome-wm](http://askubuntu.com/questions/272134/default-application-to-open-text-file-in-thunar-under-awesome-wm)

---

### Post by sideburns on 2013-09-01
As far as I know, she's on the most recent version.  However, it's actually Ubuntu with Xfce installed because Unity and Parkensen's don't go together.  (No point in doing a complete re-install just to change the DE!)

---

### Post by fadhil-hakadir on 2013-09-01
any luck?

if its ubuntu, maybe its using nautilus. How about right-click-->properties-->Open with(Tab)-->set as default(button) ?

---

### Post by sideburns on 2013-09-01
Doesn't work.  I tried that, both in the file manager and on the desktop before asking here.

---

### Post by fadhil-hakadir on 2013-09-01
sorry if i sounded like i was implying you did not try

try this:

nano .local/share/applications/mimeapps.list 

or 

gedit .local/share/applications/mimeapps.list

and under [Default Applications] type in:

application/x-ms-dos-executable=wine.desktop

then ctrl+x, y then enter

hope it works :)

---

### Post by sideburns on 2013-09-01
Thank you; I've sent the url for this thread to my sister, and we'll see what happens.  However, I'd think that there really should be a way to do this from the GUI.

BTW, I appreciate you're suggesting nano (or, "Mork's Editor," as I call it.) instead of the user-hostile vi (Fie on vi!) that some people consider the One True Editor.  Personally, I outgrew using line editors fifteen or twenty years ago, and wish they would just Go Away.

---

