---
title: "Administrators Default &quot;Open With&quot; Applications"
date: 2006-11-17
forum: General Help
---

### Post by Joshua on 2006-11-17
I'm using Edgy and I'm trying to open a *.tpl file (just text) with the script in the right-click menu called "Open as Administrator"

That will open the file with Gedit.  But I want to open it with Bluefish.  I've set the default "open with" application for *.tpl files to Bluefish for my normal user, but that doesn't seem to affect the admin settings.  I did "sudo nautilus" in the terminal and tried to set the default for the admin to Bluefish, but I get the error "Could not add application to the application database"

When I close out of that though, it looks like it adds an extra entry for Bluefish to the "open with" options for my normal user???

Any suggestions?  (Other than running "sudo bluefish [filename]" in the terminal.)

---

### Post by CatKiller on 2006-11-18
How about **gksudo nautilus**?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Joshua on 2006-11-18
Thank you.  It worked perfectly.

And, thanks for the link.  It does a great job of describing why this happens.  I'll be using sudo and gksudo much more appropriately from now on.

---

