---
title: "how would an X-Term window be setup?"
date: 2005-10-27
forum: General Help
---

### Post by susa on 2005-10-27
could someone post steps to create the equivalent of an X-Term window into a Unix server (I have the static IP address, userid and password)

---

### Post by fabiand on 2005-10-27
Hey,

how do you want to establish this connection? telnet, rlogin, ssh?

quite easy with ssh though ..: 
```
ssh -X USERID@IPADDRESS xterm
```

- fabiand

---

### Post by susa on 2005-10-27
I tried that and it fails the password

how do I enter the following

IP 123.123.123.123
userid myID
password pass

ssh -X myID@123.123.123.123 xterm

---

### Post by susa on 2005-10-27
is there any way I can run a command (anything, ssh, telnet, etc..etc.) where I can permanently store my password and connect to the unix server in a window where I can just run commands in my home folder?

on a windows systems, I use Hummingbird Exceed v10 and it opens automatically an xterm window via a script file that parses in automatically userid password and gets me to a command prompt on the unix server

surely this can be done from a linux machine - no?

assume userid: myID
assume passw: pass
assume IP add: 123.123.123.123 (or hostname host.myhost.com)

---

