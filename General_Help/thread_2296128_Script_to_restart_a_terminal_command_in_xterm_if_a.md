---
title: "Script to restart a terminal command in xterm if a server stops running."
date: 2015-09-23
forum: General Help
---

### Post by asmodaeus on 2015-09-23
So, basically, what I want to do is execute this command and make it so that, if the server shuts down, that it automatically runs the command again.

```
 sudo xterm -hold -e sudo minetest --server --worldname public1
```

Any ideas? Do I need to make a .sh file that loops itself or something like that? Thank you.

---

### Post by TheFu on 2015-09-23
If you need to run a daemon, it would be best to use the built-in OS methods for doing this.  Examples are in /etc/init.d/  Then setup a watch/monitor that checks if it is still running or not, then restarts it.

This shows how to do it with "upstart":
[https://askubuntu.com/questions/251577/how-to-supervise-and-automatically-restart-a-process](https://askubuntu.com/questions/251577/how-to-supervise-and-automatically-restart-a-process)
Please don't use this for GUI stuff. That is bad - what happens when nobody is logged in and there isn't any X/Windows server running?  It will be bad.

There is also the inittab - I'm not seeing that on a box here - ah - because upstart replaces it.  That means that systemd will replace upstart and need a new way.

---

