---
title: "Problem after installing Virtual box"
date: 2007-08-19
forum: General Help
---

### Post by PmDematagoda on 2007-08-19
There seems to be problem after installing Vbox. After i restart the computer after i install Vbox everything loads up except the the gnome application and it says in the terminal that gnome could not be loaded up. I fixed the problem by logging into my earlier kernel and deleting Vbox. After that everything weny back to normal. Does anyone know why this happened?

---

### Post by fjgaude on 2007-08-20
Seems a special kernel fix is required and a script has to be run. VMware handles all this automatically, fixing the kernel without you even knowing what happened.

frank

---

### Post by PmDematagoda on 2007-08-20
How do you suggest i can solve it?

---

### Post by chejose on 2007-08-20
Well, I just installed VB and with no problems. It sounds like you "broke" Ubuntu some way and may have to do a new installation.

I searched through their user manual (it is on their site) and followed the instructions carefully. For example they say you must start installing two packages:

sudo apt-get install libxalan110 libxerces27

If you did not do that, it could have been a cause of problems. In any case, check out the users manual with care. I am a fairly new Linus user, and have learned: Read the book first!!

By the way, VirtualBox is a fine program. I have used VM server, but VB is better.

José

---

