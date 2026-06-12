---
title: "kinda late to ask this question"
date: 2007-07-22
forum: General Help
---

### Post by brody on 2007-07-22
Hi:

I've downloaded and installed the Ubuntu server (7 point something, I think).  Installed the LAMP
option.  Pretty cool stuff.

My main use of this server  is to learn Java.  I write Delphi, VB, Smalltalk, and about a dozen assorted
mainframe languages, but have never played with Java.  Hence, installing the server.  

However, now that I'm thinking about it, should I have split the machine and put on the desktop
and then the server, or is the server standalone the right answer?  I'm currency able to PuTTY 
into the server and edit files, etc., so I don't need much other functionality as far as editing,
version control, etc.

Also, is there a special place to find the server documentation at?  I've found some, but not much.

Thanks for any help you can give me.

Brody

---

### Post by machoo02 on 2007-07-22
[Java]("http://en.wikipedia.org/wiki/Java_(programming_language)") is not a server language, even though it was developed primarily by Sun.  If you want, you can add the desktop functionality to your server very easily:```
sudo aptitude install ubuntu-desktop
```
This will give you the GNOME desktop environment.  Replace ubuntu with kubuntu if you would like the KDE desktop, or xubuntu for the XFCE desktop environment.

---

### Post by brody on 2007-07-22
Thanks for the install info Machoo, but I don't know of any compelling reason to install the desktop.  Just thought that there might be some tools or something on the desktop that would make setting up/configuring/running the server any easier.

---

