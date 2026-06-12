---
title: "Ubuntu keeps asking me to run as root, for no reason!!??"
date: 2008-05-04
forum: General Help
---

### Post by McTwist724 on 2008-05-04
Just now a small pop up box asked me to enter my root password. It says 'Run as root - Authenticate'. Every time this happens it seems like the computer lags and certain programs will cease to function, such as Amarok. I was just about to put on a new CD and it wouldn't play the song. It just froze and I had to quit.

Now, this all happened one day I was in an IRC chatroom, trying to get an invite to this site. While on there, my computer froze up and I had to restart, however, my pc would not load Ubuntu for reasons unknown to me. I had to insert my Ubuntu cd and use the option Boot from first hard disk. Does this have something to do with a virus or hacker or the like? I never enter my password cause I don't know what it is for.

EDIT:: The window just popped up again, a few seconds after I closed it. I still can't get Amarok to function properly.

---

### Post by geraldm on 2008-05-05
One thing for sure: do not provide the root password.
I would try to identify which process is causing the popup to appear.  Use the "ps aux" command to identify which processes are running.  I would leave the popup on the screen,
then take my best guess as to what process is running it, and kill the process.  The popup should disappear when the correct process is killed.  After that, check the man page for that program to find some hints on what may be happening.  

Note that a well-written program would leave no doubt that it was seeking the information, 
but a badly written program (or malware) would leave no identification for itself.
If the program is legitimate, it should nevertheless be changed to remove the vague information box. 

Gerald

---

