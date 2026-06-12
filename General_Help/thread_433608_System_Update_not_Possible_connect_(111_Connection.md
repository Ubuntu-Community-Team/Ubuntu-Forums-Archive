---
title: "System Update not Possible: connect (111 Connection refused)"
date: 2007-05-05
forum: General Help
---

### Post by daefu on 2007-05-05
Since  two days i can't connect to any repositories anymore. I can not remember to have done anything that could hurt. 
The eror-messages are:
userX@Y:~$ sudo apt-get update
Password:
[FONT="Courier New"]Fehl [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
  Konnte nicht mit localhost:8118 verbinden (127.0.0.1). - connect (111 Connection refused)
Fehl [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-de
  Konnte nicht mit localhost:8118 verbinden (127.0.0.1). - connect (111 Connection refused)
Fehl [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-de
  Konnte nicht mit localhost:8118 verbinden (127.0.0.1). - connect (111 Connection refused)
Fehl [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-de
  Konnte nicht mit localhost:8118 verbinden (127.0.0.1). - connect (111 Connection refused)
Fehl [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-de
  Konnte nicht mit localhost:8118 verbinden (127.0.0.1). - connect (111 Connection refused)
Fehl [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Konnte nicht mit localhost:8118 verbinden (127.0.0.1). - connect (111 Connection refused)[/FONT]
and so on...

why does it want to connect to localhost?. How can I see whether another program is responible for that?

I've seen (in other posts) that maybe anon-proxy might be responible. I don't have installed it (only had an firefox plugin...).

can anybody help me?

thanks in davance!

---

### Post by bapoumba on 2007-05-05
Hello,
are you behind a proxy ? Used anon proxy ?

---

### Post by daefu on 2007-05-05
> **bapoumba said:**
> Hello,
are you behind a proxy ? Used anon proxy ?

no, no proxy, not  using an anon proxy (that i know of - how could i find out?)

---

### Post by daefu on 2007-05-06
i forgot to mention: all other internet-connections seem to work properly!

---

### Post by daefu on 2007-05-08
no ideas?

---

### Post by bapoumba on 2007-05-08
Hum, I do not like to recommend this very much, but try to access ftp instead of http in your sources.list.
Sometimes, some ISP have their own proxies.

---

### Post by daefu on 2007-05-09
> **bapoumba said:**
> Hum, I do not like to recommend this very much, but try to access ftp instead of http in your sources.list.
Sometimes, some ISP have their own proxies.
thank you, i'll try this!
is it enough to simply replace http:// with ftp:// ? 


I still don't think it is a proxy outside. this is a major swiss isp, there would be more complaints. 

I think some kind of a proxy on my machin is active, but i can not detect it. 
Can i find out by inspecting running processes or in netstat? 

i use the mechanism of port forwarding through ssh-connections, but i don't have it open now.

---

### Post by bapoumba on 2007-05-09
Yes, replace http with ftp in your sources.list.

I'm not that good with networking. Others might help you better than me.

Check for proxies:
/etc/environment
.bashrc
/etc/apt/apt.conf
enter gnome-network-preferences in a terminal: is it set to direct ?

(did you play with some games that require some special settings? I recall helping someone out, that was the problem. Used some kind of IP masquerading ? Again, sorry I do not know much about this).

---

### Post by daefu on 2007-05-13
> **bapoumba said:**
> 
enter gnome-network-preferences in a terminal: is it set to direct ?

Thanks, that was it!
Some how it was set to localhost:8118

---

### Post by bapoumba on 2007-05-13
Your welcome.
Glad to see you got it to work :)

---

