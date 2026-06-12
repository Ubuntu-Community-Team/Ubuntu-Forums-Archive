---
title: "Unity and tracking of the started program"
date: 2014-03-21
forum: General Help
---

### Post by thilo2 on 2014-03-21
Hey,

does someone know how I can tell unity to track another process instead of the program which it should start via .desktop's Exec?

e.g. in the .desktop file the Exec parameter is like:
Exec=${HOME}/bin/startXYZ
But startXYZ is a script which starts another program and ends then. The other program (lets call it ABC) will be shown with another icon in unity dash (is it the dash, the program start bar?). 

Can I tell unity somehow, that it should watch the other program (ABC) instead of the startXYZ, but on click execute startXYZ?

Cheers,
Thilo

---

### Post by deadflowr on 2014-03-24
Is there a reason to go with such a roundabout way?
Why not just make the executed program the launcher?

For what it's worth I have a few applications that I like to have running when I login.
Because these seem to fight with the desktop when they load, if I start them normally, they tend to show up on the desktop all messed up.
To fix this I created a basic shell script, with a sleep option.(This stops the in-fighting that seems to happen)
I then direct the startup application entry to that script.
When the system loads, I never see the shell script running, but rather I see the application I wanted to run running.

Anyway, what do you mean by tracking?

---

