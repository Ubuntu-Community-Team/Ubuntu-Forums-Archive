---
title: "How can I test my home file server?"
date: 2007-01-05
forum: General Help
---

### Post by m.musashi on 2007-01-05
I am trying to set up a little file server using webfs. I think I have it all working but I don't know how to test it. Whenever I try to access it from firefox I get an "unable to connect" error. My thought is that for some reason I cannot use an http protocol to come into my own network but I don't know why that would be the case. I've also tried using proxy sites to make it look like I'm coming from somewhere else but that didn't work either.

Does anyone know a way for me to view my own file sever from inside my own network?

Thanks.

---

### Post by kd7swh on 2007-01-05
Are you behind a firewall or router? Port forwarding may be helpful.

---

### Post by m.musashi on 2007-01-05
Thanks for the reply. Yes, I have a router/firewall but I have configured it to forward the proper port for webfs. However, I'm wondering if that won't make much of a difference if I try to access from within my network. I don't know enough about networking to know if and how I can access a file server on my computer without using some external network. I'm not sure I'm making any sense but hope it does.

Thanks.

---

### Post by koenn on 2007-01-06
how do you connect to it ? By typing something in firefox address bar ? What exactly ? A server name ? Can you try it using the server's IP address ?

---

### Post by m.musashi on 2007-01-06
Thanks for the reply. The "server" is nothing more than a folder on /home that has been made available to the web with the webfs app. Webfs listens on port 8000 and connects to whatever folder I assign. In this case it's /home/share. I changed the permissions with chmod to 755 (also tried 777 but didn't help). I forwarded port 8000 to my computer and even added a rule in firestarter to allow traffic on that port. I had this working before but for some reason after reinstalling edgy it won't (yes, I reinstalled webfs and edited the conf file). My /home is on a different partition so it was not reformatted during the reinstall if that could make a difference.

In order to test it, I use firefox and typed localhost:8000 in the address bar. I get an "access denied" error when I do that. Sometimes it tellls me it "cannot connect". From an external connection I have set up a dynamic dns through dyndns but that shouldn't have anything to do with me being unable to connect via localhost. I also checked the /etc/network/interfaces and /etc/hosts to make sure localhost was there.

What I can't figure out is why I can't loopback into my shared folder. If anyone sees the error of my ways please let me know.

Thanks.

---

### Post by Tenicus on 2007-01-06
Have you tried connecting via a proxy server to see if its only from your LAN IP that it doesnt work?

---

### Post by koenn on 2007-01-06
> localhost:8000 in the address bar. I get an "access denied"
does sound like a permissions problem.
do you know, from the documentation or by looking in /etc/passwd; which account webfs runs under ? 
could you, just for testing, set 777 on /home as well as on /home/share - maybe it's possible the permissions on /home prevent traversing to /home/share

to rule out network problems : run the following in a terminal: 
```
telnet 127.0.0.1 8000
```
If you don't get a time out or connection refused or something similar, you're probably ok. 
if you get a reply that looks like it could be comming from webfs, you're defenitely ok, network-wise

---

### Post by m.musashi on 2007-01-06
> **Tenicus said:**
> Have you tried connecting via a proxy server to see if its only from your LAN IP that it doesnt work?

Yes, I tried that but it didn't work either.

> **koenn said:**
> does sound like a permissions problem.
do you know, from the documentation or by looking in /etc/passwd; which account webfs runs under ? 
could you, just for testing, set 777 on /home as well as on /home/share - maybe it's possible the permissions on /home prevent traversing to /home/share

to rule out network problems : run the following in a terminal: 
```
telnet 127.0.0.1 8000
```
If you don't get a time out or connection refused or something similar, you're probably ok. 
if you get a reply that looks like it could be comming from webfs, you're defenitely ok, network-wise

telnet gave ```
jim@edgy:~$ telnet 127.0.0.1 8000
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
Connection closed by foreign host.
``` and then kind of hung. Is that what it should do?

I chmod'd /home to 777 and now it works so it's obviously a permission problem. However, do I really want /home to be 777? Is that a little unsafe?

---

