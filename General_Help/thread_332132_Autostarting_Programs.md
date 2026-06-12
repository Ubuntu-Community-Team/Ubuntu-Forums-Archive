---
title: "Autostarting Programs"
date: 2007-01-05
forum: General Help
---

### Post by Duffy on 2007-01-05
I have a program (Sambar) that is a web, mail, IRC, Jabber, FTP, etc. server.  It is installed in the /usr/local/sambar/ directory.  The vendor requires that to start the program you have to start it as root or su.  So when I start the program, I have to start it from a terminal by logging in as a su in a terminal window.  I change directory to /usr/local/sambar/bin/ and then enter ./server to start the program.  This works o.k. in Kubuntu, but with Ubuntu, whenever I close the terminal window, the server shuts down. That does not occur with Kubuntu however.

Two things I would like to be able to do. First, log in as a regular user and then click on an icon on the desktop with the path /usr/local/sambar/./server but that never seems to work even when installed on Ubuntu and logging is as the root user (yes I am able to log in as root as I set up Ubuntu to allow me to log in as root).

Second, I would like to have the program autostart whenever I start/re-start the system. The vendor has provided an init script but I am not sure where to place the script in Ubuntu or Kubuntu (I am running both) to get it to work.

I have been used to running the same server on Windows by simply dragging the sambar icon and dropping it into the startup folder on Windows. I wish it was that easy on Ubuntu/Kubuntu. 

Can anyone guide me on how to accomplish starting it from the desktop and especially being able to start it automatically when Ubuntu/Kubuntu starts up?

Thanks,

Duffy

---

### Post by Mithrilhall on 2007-01-05
To have it auto-start...edit...


```
nano /etc/rc.local
```

This is how I start freepops when the computer starts.

---

### Post by Duffy on 2007-01-05
Thanks, but how do I actually do it? I've read some documentation trying to figure it out from your suggestion, but it is confusing to us non-programming types.

---

### Post by NumberOne on 2007-01-05
put the command that you use in terminal to start the program in the rc.local file.

---

