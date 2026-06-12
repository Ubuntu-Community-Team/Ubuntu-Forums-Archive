---
title: "VNC sever help"
date: 2007-07-12
forum: General Help
---

### Post by Mostlyharmless42 on 2007-07-12
Currently i can connect from my windows machine to my linux desktop, the mouse works, but i can't type.  Does anyone know how to fix that?? 
Or can anyone tell me how to get tellnet to work???

---

### Post by HermanAB on 2007-07-12
The secret is SSH.  That is a secure telnet replacement:
$ ssh username@192.168.1.2

The SSH daemon is enabled by default on most all *nix computers and is the main way in which machines world-wide are managed.

On Windoze you need a program called PuTTY:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

'Hope that helps!

Herman

---

### Post by Mostlyharmless42 on 2007-07-13
when i use putty on windows i type in my IP address in the box labled "host name (or IP address) and i leave the port set to 22 which is the default.  It gives me and error box that says "netork error: connection refused"

---

### Post by Mostlyharmless42 on 2007-07-13
bump

---

### Post by DaveAK on 2007-07-13
Chances are that port 22 is not open on your Ubuntu machine.  I'm a total newbie so don't know how to check this or fix it.

---

### Post by pmg on 2007-07-14
It's also possible you don't have **sshd** (the server end of ssh) running.  From a terminal run the command **ps ax | grep sshd** and if it shows "/usr/sbin/ssh" it's running.  (It will probably show the "grep sshd" command also.  Ignore that.)

If sshd is not running, to start it this one time from the terminal window run **sudo /etc/init.d/sshd start**.  To set it up to start whenever you boot go to the pulldown System -> Admin -> Services and check the box by "Remote Shell Server (ssh)".

---

### Post by marsbt on 2007-07-14
oh, also make sure open-ssh is installed (or ssh .... which should give you both openssh-server and openssh-client). You will get a connection refused even if there is no sshd running on port 22 on the remote host.

---

