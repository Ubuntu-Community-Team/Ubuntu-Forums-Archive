---
title: "Free Portable Web server (PHP + DB) without intallation"
date: 2020-01-29
forum: General Help
---

### Post by alain.roger on 2020-01-29
Hi,

i've used several years webserver (XAMPP) to do my local development. However this has some issues when i need to change my computer and use my laptop, or when my NAS is not reachable when i do not have internet connection.

So in order to avoid to recreate the same local development environment on all computers as to avoid issue while i do not have internet connection, i'm looking for a way to have a portable web server that includes SSL, database, PHP and so on...
The basic idea is to have a local development environment, always available and in case of need transportable and synchronizable among computers (or at least usable)

I found that USBserver exists but it is not free.

So any idea where to start, or what to do would be very appreciated.

thx

---

### Post by dragonfly41 on 2020-01-29
I can suggest the [Atom editor]("https://atom.io/") which I use.
But be advised that it is *too hackable*.
That is. there are hundreds of packages to understand and experiment with.
For your development install php-server. This launches a localhost server to preview your content.

---

### Post by alain.roger on 2020-01-30
In fact, it is just for my purpose to develop and to be free without being forced to re-create the same web server on each new machine where i am. SO basically i do not need a complete server, only PHP, SSL, DB and debugger basically.

---

### Post by dragonfly41 on 2020-01-30
Then just search "install LAMP Stack on Ubuntu 19.04".

[https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/](https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/)

---

### Post by alain.roger on 2020-01-30
i already knows how to install xampp so thats not the point hereas lamp stack is installed with hard coding of path where installations are...mainly in opt...and this is in fact what i'm trying to get rid off... for exalple i would like to have  lamp stack but without any installation... only files in a directory and i could run a shell script to start all servers (db,php, apache) but in one and only one folder...
the problem of xampp it is that installation needs root permission and i want to avoid it

---

### Post by dragonfly41 on 2020-01-30
I understand better. The key word is portable.

As suggested in[ this old thread (which I see you started)]("https://ubuntuforums.org/showthread.php?t=2299081") use a virtual machine?

[Later thought][ Docker LAMP container?]("https://linuxconfig.org/how-to-create-a-docker-based-lamp-stack-using-docker-compose-on-ubuntu-18-04-bionic-beaver-linux")

---

### Post by alain.roger on 2020-01-30
A virtual machine means to sync between computers a huge amount of GB as even a LAMP installation in VM is huge. When i worked under WIndows, i created my own LAMP stack portable. However under Linux librairies are dependent and this is an issue to do a real portable version.
Docker LAMP container is AFAIK an isolated installation of LAMP but it is still a huge amount of GB to move from 1 computer to another...at least if i read it correctly.

i was expecting to have a portable apache or NGNIX, portable php, portable MySQL and SSL... under windows it is possible, so i do not understand that Ubuntu does not allow it...without root privileges

---

### Post by Holger_Gehrke on 2020-01-30
I have no experience with it, but rolling your own [AppImages]("http://appimage.org") seems like it would allow you to do what you want. AppImage was basically developed as portable apps for Linux. Don't know about running servers as AppImages, those should normally run in a different user for security reasons ...

Holger

---

### Post by dragonfly41 on 2020-01-30
[This is portable.]("https://www.raspberrypi.org/forums/viewtopic.php?t=218354")

---

