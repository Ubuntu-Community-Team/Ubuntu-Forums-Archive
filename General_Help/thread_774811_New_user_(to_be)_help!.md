---
title: "New user (to be) help!"
date: 2008-04-29
forum: General Help
---

### Post by meru on 2008-04-29
I am trying to determine which version of Ubuntu I should use.... moving from Windoze XP which is presently also running as a http and ftp server and the rest of the use is primarily desktop functionality.  I am experimenting and would like to install Ubuntu on a machine - no dual boot - which would mimic my windoze xp installation.  I want to see how easy it is to run my web and ftp servers on Ubuntu and maintain.  Should I go with the desktop or should I opt for the server?  I am planning on going with 8.04.  Any advice I can get will be really truly and greatly appreciated.

Thank you very much.

...Ibrahim Meru

---

### Post by Rainstride on 2008-04-29
as far as i know the server dosen't have any type of GUI so if you want windows like use go for desktop and ad on server fuctional(dont ask me how, i just know you can....somehow).

---

### Post by ebelog on 2008-04-29
As a user more comfortable with Windows, you'll probably have the best luck with the desktop version which will include the graphical interface and management tools by default. You'll still be able to configure it as a web server and ftp server, because those are just additional software packages that you can install.

---

### Post by chrisccoulson on 2008-04-29
I probably can't be much help, but bare in mind:
[LIST]
[*]If you go with the server edition, you don't get a GUI (although it's easily installable)
[*]Likewise, if you go with the desktop edition, you don't get the server stuff. But again, I think it's easy to install
[/LIST]

So, if you want to use the machine as a desktop and a server, it probably doesn't matter which edition you go for - you'll still have to install extra stuff. The amount of work will be pretty equal.

If you are just using it as a server, then the choice is obviously the server edition.

---

### Post by meru on 2008-04-29
Thank you Rainstride, Ebelog, and Chrisccoulson for your assistance.  Based on your feedback, I chose to download the desktop and hope to start playing with Ubuntu shortly.

Thanks very much. 

...Ibrahim Meru.

---

### Post by rturner on 2008-04-29
After you set up the desktop, installing a lamp server with httpd, mysql and php is incredibly easy.

```
sudo tasksel install lamp-server
```

[A more complete how-to page:]("https://help.ubuntu.com/community/ApacheMySQLPHP")

I use my Hardy desktop install as a testing web server on my LAN.

---

