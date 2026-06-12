---
title: "running a mono program though xterm"
date: 2015-08-26
forum: General Help
---

### Post by dave193 on 2015-08-26
Hey all, 

I've been using a Linux server for a few years now and have occasionally had need of running graphical programs on my mac using x11 with ssh -X forwarding. I have a program that runs a backoffice for a restaurant POS that I use like this:

ssh -X <my ip address> warehouseopenplus

This works fine (I have rsa keys set up and a host file hence no passwords / usernames). I am trying to replace this program with one called IncoPOS which is a fork of the same opensource code. This program uses the mono framework and here is where my knowledge of the whole thing starts to fall apart. Warehouse Open Plus runs as warehouseopen and hence I launch it from the command line that way. I can't figure out how to launch IncoPOS or where it is installed and in the task manager it's running just as "mono" with the IncoPOS icon. 

How do I run this program via ssh -X ??

Thanks for any help you can give!

---

### Post by TheFu on 2015-08-26
Please post the output/errors here.

---

