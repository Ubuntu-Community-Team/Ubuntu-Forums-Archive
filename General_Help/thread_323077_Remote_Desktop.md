---
title: "Remote Desktop?"
date: 2006-12-21
forum: General Help
---

### Post by kbaum on 2006-12-21
I need a way to connect to another Ubuntu PC over the internet (not over a LAN). Is this possible?

---

### Post by bernied on 2006-12-21
ssh will give you a secure terminal (command line). If you want a Desktop environment, the easiest way is to use vnc. On its own, vnc is not very secure, but you can 'tunnel' the vnc session through an ssh session - this is considered safe.

Here's some links:
[http://www.realvnc.com/what.html](http://www.realvnc.com/what.html)
[http://www.openssh.com/](http://www.openssh.com/)
[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)
[http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

---

### Post by fragos on 2006-12-21
Many ISPs give you a dynamic vs static IP connection to the internet.  You'll need the actual IP when when connecting because your local connection doesn't have an domain name associated with it.  You'll need to set up a dynamic DNS to be identified over the Internet.  Free ones are available from a number of sources.  I use [www.changeip.com](www.changeip.com) to provide that service for me.

---

