---
title: "Allow remote desktop automatically"
date: 2022-06-08
forum: General Help
---

### Post by pety2do on 2022-06-08
[FONT=Arial]Hi, I’ve installed TeamViewer on my laptop (Windows 10) and my PC (Ubuntu 22.04), I already have turn on the unattended access but every time I try to access from Windows to Ubuntu I get a message asking me permission to conceed access to remote desktop… I’ve already check the Remote Control config on Ubuntu but I can’t use benefit of unattended access… Is there any way to get it?
I have no problems with unattended access from Ubuntu to Windows, just when I try to access to Ubuntu…[/FONT]
[FONT=Arial]Thaks for your help and sorry for my english…[/FONT]
[FONT=Arial]Regards…

This is the message I get whenever I try to connect:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290591&stc=1[/IMG][/FONT]

---

### Post by TheFu on 2022-06-08
x2go runs as a service on Linux and starts before any user logs in.  It is easy to remotely access the system using x2go.
[https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

x2go uses ssh for user authentication and encryption of all traffic between the client and server.  Also, it doesn't work with Gnome 3+ or KDE-Plasma, so any other DE or WM needs to be used with it.  I've used x2go from 5 different continents over the years. It works better than any other solution with much greater security.  But the remote server must be accessible using ssh for x2go to work.  Once ssh-keys are setup, it works crazy easy and is extremely optimized for performance when compared to all other remote desktop solutions.

There is an x2go client for Windows. I used it daily for a few years before switching almost 100% to Linux on my desktop.  Once ssh-keys are exchanged between the client and server, there won't be any need to ask permission.  Even without keys exchanged, the remote system isn't involved in granting access to the current X2go session.

---

### Post by couzin2000 on 2022-06-11
> **pety2do said:**
> [FONT=Arial]Hi, I’ve installed TeamViewer on my laptop (Windows 10) and my PC (Ubuntu 22.04), I already have turn on the unattended access but every time I try to access from Windows to Ubuntu I get a message asking me permission to conceed access to remote desktop… I’ve already check the Remote Control config on Ubuntu but I can’t use benefit of unattended access… Is there any way to get it?
I have no problems with unattended access from Ubuntu to Windows, just when I try to access to Ubuntu…[/FONT]
[FONT=Arial]Thaks for your help and sorry for my english…[/FONT]
[FONT=Arial]Regards…

This is the message I get whenever I try to connect:[/FONT]

I've had the same exact problem. Apparently, something in Teamviewer got broken around version 15.25. According to a site I just read we're supposed to try to downgrade the version of Teamviewer on Ubuntu to 15.18.4. The command they said to use was [FONT=Courier New]sudo apt install teamviewer=15.18.4[/FONT]. However I have tried and I get the same message everytime, package cannot be found. I'm trying to add the Teamviewer repo, and there's no way to install the gpg keys - the commands won't work. So I'm stuck trying to find a different client version .deb file.

---

