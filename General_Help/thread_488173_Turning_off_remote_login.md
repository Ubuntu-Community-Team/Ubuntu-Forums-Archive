---
title: "Turning off remote login"
date: 2007-06-29
forum: General Help
---

### Post by Xs1t0ry on 2007-06-29
Hi

Out of curiosity, I decided to enable remote login in the options. After this, I can't access my desktop, only a console. When I refresh my desktop the screen goes black and the loading circle appears and it stays like that until I hit <ctrl><alt><F1> which brings me back to the console, where, if I choose, I can login (remotely?). 

I have been searching, but** need you're help in finding the console cmd to disable remote login. **

Thanks!

---

### Post by Scunizi on 2007-06-29
vino-server is the process you want to kill.  you can find the pid # by typing "pidof vino-server" then type "kill (and the number).  However I just tried it and it automatically restarts.  You can't CTRL+ALT+F7 to get back to the gui? or /etc/init.d/gdm start?

---

