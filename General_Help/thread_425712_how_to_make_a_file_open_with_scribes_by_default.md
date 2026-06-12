---
title: "how to make a file open with scribes by default"
date: 2007-04-27
forum: General Help
---

### Post by jinxjinx on 2007-04-27
how do i make all txt files and all documents open with scribes by default?

Thanks

---

### Post by mac.ryan on 2007-04-27
right click --> **properties **--> open with

Then you can add a compatible app and select it as default one.

---

### Post by jinxjinx on 2007-04-27
wont let me "add" any apps, not even when i open nautilus as root. says "Could not add application to the application database" or when i use nautilus as a regular user, scribbles shows up but it wont let be click it...

---

### Post by mac.ryan on 2007-04-27
Can you post here a screenshot of the "scribbles"?

---

### Post by jinxjinx on 2007-04-27
heres a screen shot, i guess its called scribe...not scribbles

---

### Post by AlexenderReez on 2007-04-27
something wrong with that software itself...which version of scribes you are using?i'm using from getdeb.net..seems ok...

---

### Post by jinxjinx on 2007-04-27
actually it wont let me select any application, not just scribe

---

### Post by mac.ryan on 2007-04-27
First, just to check out reez0105's idea, see if the operation you attempted with scribe works for other stuff. For example, install some image viewer and see if you can edit an image properties field...

If the problem persist, then I would say it is linked to gnome. I don't have a solution for that, but I would try working on the gnome application database for example rebuilding the MIME cache:
[LIST]
[*]removing (after backup!) **/usr/share/applications/mimeinfo.cache**
[*]running **update-mime-database**[/LIST]and then trying to re-set scribe to open txt files...

Another text you can run is to see if another test user you create can perform the same operation you want to. If that user can, then the problem must be in some of your profile settings (normally under /home/<username>/.gnome and .gnome2...

Just ideas... but I can't replicate the bug on my system so... :(

---

### Post by mac.ryan on 2007-04-27
Anyhow: a good reading for understanding how to operate on the application database is the gnome manual:

[http://www.gnome.org/learn/admin-guide/latest/mimetypes-0.html](http://www.gnome.org/learn/admin-guide/latest/mimetypes-0.html)

if you find a solution, please report it... I am very curious now! :)

---

