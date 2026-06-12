---
title: "Ubuntu 7.10 KDE and Xming"
date: 2008-04-11
forum: General Help
---

### Post by ubuopensvr on 2008-04-11
Hi there

I have installed kubuntu-desktop and want to connect using xming on this server from my laptop. I have setup the access by editing the 2 files

sudo vi /etc/kde3/kdm/kdmrc

sudo vi /etc/kde3/kdm/Xaccess

I have started kdm via /etc/initd/kdm start

then ps -ef | grep 177 and it looks ok

8420  8284  0 13:01 pts/1    00:00:00 grep 177

when i run Xnest - query localhost :1 i get error

Xlib: connection to ":0.0" refused by server
Xlib no protocol specified

unable to display ":0.0" fatal server error

can anyone help

---

