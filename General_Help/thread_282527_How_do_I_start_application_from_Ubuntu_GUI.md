---
title: "How do I start application from Ubuntu GUI"
date: 2006-10-22
forum: General Help
---

### Post by kodachrome64 on 2006-10-22
I just compiled a program and to run it I need to enter this in the terminal to start it.

sudo /usr/sbin/application_name

I'd like to just type "application_name" in the terminal instead. 

Better yet I'd like to be able to use the Ubuntu GUI to start the app. How do I set this up?

---

### Post by newlinux on 2006-10-22
If it is a graphical app I think you could add it via the a la carte menu editor or right click the desktop and choose Add Launcher.

Put in ```
gksudo /usr/sbin/application
```

One or both of those should work...

---

### Post by bionnaki on 2006-10-22
do this to:

> sudo nano /usr/bin/applicationx

copy/paste:

> #!/bin/sh

/path-to-application/applicationx $*


and save/exit

and then make it executable:

> sudo chmod +x /usr/bin/applicationx

applicationx would be the name of your application of your choice.

then all you have to do is enter applicationx as the command & it'll run

---

