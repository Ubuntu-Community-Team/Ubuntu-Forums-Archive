---
title: "Can't connect to FTP"
date: 2008-07-10
forum: General Help
---

### Post by DougAlder on 2008-07-10
Here's the message I get from gFTP when I try and connect to my server

Looking up 209.97.221.xxx
Trying 209.97.221.xxx:21
Connected to 209.97.221.xxx:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 21:29. Server port: 21.
220-This is a private system - No anonymous login
220 You will be disconnected after 15 minutes of inactivity.
USER foo

331 User foo OK. Password required
PASS xxxx
230-User foo has group access to:  foo
230 OK. Current restricted directory is /
SYST

500 ?
TYPE A

215 UNIX Type: L8
PWD

200 TYPE is now ASCII
Invalid response '2' received from server.
Disconnecting from site 209.97.221.xxx


I've also tried connect to server from the Places menu and it won't connect either. If I drop out of Ubuntu and boot back into windows I can connect just fine. Anyone have any ideas what's going on here? I thought t first it might be something in iptables on this end but I ran iptables --flush, as well as set up rules allowing anything from my server

---

### Post by DougAlder on 2008-07-10
Maybe it will help to know that when I try and use the upload feature in Wordpress and to upload a file from my Ubuntu partition it times out and I get an error message from Wordpress that say "http error"

---

### Post by BlackDog71 on 2008-07-22
Hello, I have the same problem. Anyway it only happens with some ftp servers. Some are working, some aren't and I could not find a clear answer for that.

---

### Post by DougAlder on 2008-07-22
> **BlackDog71 said:**
> Hello, I have the same problem. Anyway it only happens with some ftp servers. Some are working, some aren't and I could not find a clear answer for that.

I've given up on it - I just use Places - Connect to Server now.

---

### Post by lamego on 2008-07-22
Have you checked your ftp server logs somewhere under /var ?

---

