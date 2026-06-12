---
title: "'Convert' Ubuntu Desktop  to Server?"
date: 2013-02-10
forum: General Help
---

### Post by candtalan on 2013-02-10
A friend asked how a desktop installation of Ubuntu could be made to work as a server (lamp stack). I had no real idea (novice here) and I noted that most searches for comments showed that people were in fact asking for the other way round - starting with a server install and then ading GUI. Is it easy to add a 'lamp server' package install to Ubuntu.......?
tia

---

### Post by nothingspecial on 2013-02-10
Ubuntu is a gigantic collection of packages.

Desktop Ubuntu is one mixture of them

Ubuntu Server is another

Lubuntu is another  etc etc

Whatever you start out with, you can install (or remove) any of the available packages in the Ubuntu repositories.

---

### Post by ahallubuntu on 2013-02-10
~

---

### Post by MAFoElffen on 2013-02-10
> **candtalan said:**
> A friend asked how a desktop installation of Ubuntu could be made to work as a server (lamp stack). I had no real idea (novice here) and I noted that most searches for comments showed that people were in fact asking for the other way round - starting with a server install and then ading GUI. Is it easy to add a 'lamp server' package install to Ubuntu.......?
tia

As other's have said, you can install/config Ubuntu Server service packages on Desktop... Just as you can install desktop packages to Server.

Underlying those, there are some differences in the base Linux systems. Desktop Edition, the base Linux system is optimized for graphics and user interactions. No-one wants to wait for the cursor to move across a screen or to see the letters they type appear on the screen. In the Server Edition, the base Linux system is optimized for prioritization of server services and background processes...

So, you can run server services on desktop, but it will not perform those services as "well" as it would if they installed it on a system optimized for those services (server edition). BUT- if it is not in a production environment, the average user may not be able to load it down enough to even notice that.

I have one desktop here setup with server services so I can develop and debug web or network applications, attaching to the server services through "local" as if it was somewhere else, but not affecting the rest of my network in doing it.

---

### Post by tgalati4 on 2013-02-10
Look for an out-of-warranty Dell PowerEdge server on Craigslist.  Then install the server version.  You will soon see the differences in performance between using a desktop install and a true server install on real server hardware.  For home use, simply adding services to a Desktop is convenient.

---

### Post by dcstar on 2013-02-11
> **candtalan said:**
> A friend asked how a desktop installation of Ubuntu could be made to work as a server (lamp stack). I had no real idea (novice here) and I noted that most searches for comments showed that people were in fact asking for the other way round - starting with a server install and then ading GUI. Is it easy to add a 'lamp server' package install to Ubuntu.......?
tia

Be very sure that you want the system to be one or the other, for example the Server kernel does not support audio because audio is an unnecessary waste of resources in a server environment - it is optimised for Server tasks.

A Desktop is a Desktop with all the things Desktop users expect, a Server has different things because it does a different job.

---

### Post by Cheesemill on 2013-02-11
> **MAFoElffen said:**
> Desktop Edition, the base Linux system is optimized for graphics and user interactions. No-one wants to wait for the cursor to move across a screen or to see the letters they type appear on the screen. In the Server Edition, the base Linux system is optimized for prioritization of server services and background processes...

> **dcstar said:**
> Be very sure that you want the system to be one or the other, for example the Server kernel does not support audio because audio is an unnecessary waste of resources in a server environment - it is optimised for Server tasks.

This used to be true but it isn't anymore.

Ever since 12.04 both Server and Desktop use the same kernel.

[https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)

---

### Post by candtalan on 2013-02-11
Thanks for the responses, much appreciated.

---

### Post by msandoy on 2013-02-11
Just open a terminal and type "sudo tasksel". Then you choose the server tasks you want to have installed.
Here is a guide for step by step instructions:
[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

---

