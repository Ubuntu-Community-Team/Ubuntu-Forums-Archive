---
title: "Issue with -daemon command or such"
date: 2018-04-19
forum: General Help
---

### Post by tept945 on 2018-04-19
Did apt update and apt upgrade on a new 16.04 VPS

downloaded a zip file that I then unzipped and entered the dir that the file unzipped to

Instructions for what I'm doing gave me 3 commands to do at this point

chmod 777 seraphd
chmod 777 seraph-cli

and then the 3rd command

./seraphd -daemon

The error I get at this point is 

./seraphd: error while loading shared libraries: libboost_system.so.1.58.0: cannot open shared object file: No such file or directory

Sorry if this is too vague, this is literally all the steps I've taken so far and were instructed on the walkthrough and I am very new to Ubuntu


[https://www.youtube.com/watch?v=gQmTg0Q97qQ](https://www.youtube.com/watch?v=gQmTg0Q97qQ)

That is the link to the tutorial I was following along to, replacing solaris with seraph.

Thanks in advance.

---

### Post by kerry_s on 2018-04-19
in terminal:
apt search libboost

see what has that & install

---

