---
title: "How make BASH on Ubuntu 20.04 ..."
date: 2020-08-26
forum: General Help
---

### Post by paulgureghian on 2020-08-26
free a specific port (3000) in this case, after stopping a running  Go server in the terminal ? 

I make a code change, then stop the server, recompile and run. but the server wont serve again until

I close and reopen the terminal. 

Thanks

---

### Post by TheFu on 2020-08-27
A properly written server should accept a -HUP signal, reread any config files and restart.
When modifying code used IN the server itself, having the server stop, then start should be sufficient. A shutdown process will free system resources automatically. I suspect the method you are using isn't actually shutting down the server.

Please show exact start and stop commands.

---

### Post by paulgureghian on 2020-08-27
**I hit  Ctr - Z to stop the server, then I do    'go build . && ./Go_Webserver'  to restart. **

---

### Post by TheFu on 2020-08-27
cntrl-z isn't ending the process. It pauses it.  If you type "bg", that will put the stopped process in the background it will detach from the parent (the current shell) and continue running.  This is expected "job control" for almost every Unix shell in the world.
[http://www.linuxcommand.org/lc3_lts0100.php](http://www.linuxcommand.org/lc3_lts0100.php) explains and has examples.

To end the process, use cntl-c.

When you do ./Go_Webserver, you have just spawned an new process, leaving the old one paused, eating RAM, open files, and system resources.  Bad, bad, user.  It doesn't "restart" anything.

---

### Post by paulgureghian on 2020-08-27
**Yup, just did Ctrl-C and it stopped the server and then I was able to restart the server. **

---

