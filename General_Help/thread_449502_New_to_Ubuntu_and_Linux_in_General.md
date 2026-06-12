---
title: "New to Ubuntu and Linux in General"
date: 2007-05-20
forum: General Help
---

### Post by a_user on 2007-05-20
Hello all,

I am sure this is going to sound like a very beginnerish question, but I am fairly new to linux and especially working only from a command line. I am trying to configure ubuntu version 6.06 server to run vmware server. What I cant figure out is how to download files from the internet using only the command line? Is this even possible? How does someone go about getting files from a web page onto the server? Does it have to be downloaded from another PC and then copied over? I realize firefox is not installed by default with the server configuration, so is there another browser available that can be opened from the console to do this?

Thanks for the assistance :redface:

---

### Post by rich.bradshaw on 2007-05-20
Use wget

eg 

wget internetaddressoffile

---

### Post by rich.bradshaw on 2007-05-20
lynx is a browser, elinks might be better.

Have you used Linux before? If not, I'd recommend starting with the normal version so that you have a GUI...

---

### Post by FryerFox on 2007-05-20
The normal (desktop) installation is not unsuitable for use as a server. At my company, when we send out servers, we use the standard Dapper (6.06) installation and then add/enable/remove/disable the stuff we want with a basic script.

But it definitely is possible to get around using just the command line. What specifically are you trying to download (path, filename)?

---

### Post by ItaniKnight on 2007-05-20
I'd be very interested to know how you do that. I've got the desktop AND server versions installed (well, Xubuntu desktop and Ubuntu server) and I have absolutely no idea what to do with the command line... So, any tips on how to turn the desktop version into a web server will be hugely appreciated ;) Especially if you can actually get to it from the internet...

---

### Post by rich.bradshaw on 2007-05-20
The only difference between desktop and server is the addition of a GUI really, they are both very very very similar otherwise.

If you want to go from server to desktop,

sudo apt-get install ubuntu-desktop

This link [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) is about how to make a server in ubuntu, boils down to

sudo apt-get install apache2

then anything in /var/www is served. If ports are forwarded, that's accessible on the internet. Type localhost into address bar in Firefox to see it in action....

---

### Post by FryerFox on 2007-05-20
Rich said it better than I could.

Basically, setting up a web server, mysql, php, etc. is a completely seperate task than installing Ubuntu. All (full) Linux distributions have apache web server packages available.

---

