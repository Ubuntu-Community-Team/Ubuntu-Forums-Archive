---
title: "*trying* to run ubuntu server - Apache Errors"
date: 2007-09-21
forum: General Help
---

### Post by xelapond on 2007-09-21
OK, so, I set up my server, and installed and configured Subversion.  I have never used apache before.  I tried to restart apache and it complains there is no pid file.  After this another thing pops up saying:

(98)Address alreardy in use: make_sock:could not bind to address 0.0.0.0:80

Here is what it says completely:

*Forcing reload on web server(apache2)
httpd(no pid file) not runnning
(98)Address alreardy in use: make_sock:could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Any ideas?  I did not mess with apache2.conf, but if there are any changes i need to make i know how.  Also, All i am trying to do is run a Subversion server with web access.

Any help would be greatly appreciated.

---

### Post by jamvegan on 2007-09-21
Hi there.  You didn't get any permission denied messages?  I ask because the error you posted is exactly what I get if I try:
```
/etc/init.d/apache2 restart
```
instead of:
```
sudo /etc/init.d/apache2 restart
```
The only difference is that I also get a permission denied message.

---

### Post by lavajumper on 2007-09-21
> **xelapond said:**
> 
*Forcing reload on web server(apache2)
httpd(no pid file) not runnning


->This happens when the shutdown script can't find the file containing the process id of apache2

> **xelapone said:**
> 
Address alreardy in use: make_sock:could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs


->Now, Apache is trying to restart, but the old process has bound to port 80, so the new process cannon bind to listen...and Apache gives up. 

You probably have some other process listening on port 80:

Try issuing: 'netstat -anutp |grep 80' in a terminal and look at the output to see what process is in a LISTEN state on port 80, and stop it or kill it.

If apache2 is listening on port 80 you need to make sure all apache processes have stopped, and port 80 has been released before you can start a new apache. Try issuing: 'sudo killall apache2' from a terminal session to make sure all apache2 processes are terminated, then issue 'sudo /etc/init.d/apache2 start' to start the new servers.
 

If these suggestions don't work, come post more.

Good Luck!

---

### Post by lavajumper on 2007-09-21
#-o
Reading a little closer, Jamvagen is also correct. The restart, stop and start commands must be run as root.

---

### Post by xelapond on 2007-09-21
OK, so i fixed that issue, and web access works, but whenever i try to access its URL over a subversion program io get this error:

PROPFIND request failed on '/'
PROPFIND pf '/': 500 Server livence expire ([http://***server](http://***server) url here***)

Any ideas?

---

### Post by xelapond on 2007-09-21
As well as the previous errors mentioned when i try to get on to the web client it says:

500 Server license expired

Any help would be appreciated greatly.

---

