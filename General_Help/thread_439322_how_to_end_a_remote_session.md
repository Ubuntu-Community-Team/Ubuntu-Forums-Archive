---
title: "how to end a remote session?"
date: 2007-05-10
forum: General Help
---

### Post by cybergalvez on 2007-05-10
Hi I've to a newbie question.  I just installed ubuntu on an experiment server, and I am connecting to it from my windows box using cygwin.  To do that I use the startxwin.bat file to open up an xserver with xterm, I then ssh -Y user@ubuntu to log into my ubuntu box and then I run the command gnome-session & to launch my gnome desktop.  All this works well, except how do you logoff? If I use the logoff button everything hangs, and if I close my xterm window it leaves the session running? is there a way to either gracefully close the session properly or log back into the next time? Right now phantom processes are building up with my name attached to it. (which don't happen if I log in and off at the terminal)  Thanks in advance for any and all help
Jose

---

### Post by stylishpants on 2007-05-10
Just type "exit" and hit enter.  
"Ctrl-d" should work too.

---

