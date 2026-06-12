---
title: "remote management"
date: 2007-11-25
forum: General Help
---

### Post by deamon_knight on 2007-11-25
I'm setting up a linux desktop on an old box for a someone who isn't computer savvy and doesn't want me to spend any money on the project. I'm still learning Ubuntu but Xubuntu looks like to way to go. I've installed everything I want and the desktop is configured as I need it but I need to see if some features are available.

Is there anything like large icons in Gutsy? This is for an elderly relative and if I can make the text easier to read it will be helpful. High contrast large Icons is ugly, plain and simple, but i can't find a theme that will change Fonts across the whole system. Is there any way to do this?

Question two: I believe Microsoft tech support can log in to a windows computer and administer it remotely while the user can still observe what is going on on the desktop. Is there anyway to do this in Xubuntu? Remote desktop session as I understand them will log the current user out of the system. I need to be able to demonstrate how to do things remotely (My relative is 300 miles away!)

Thanks

---

### Post by wieman01 on 2007-11-26
As for your second question (I cannot answer the first one as I run KDE... there it is definitely possible to change icon size), yes, you would have to install a VNC server on the target PC and a VNC client on your PC for remote maintenance.

KDE (Kubuntu) comes with a default remote desktop software.

This is something for Gnome:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/")

---

### Post by deamon_knight on 2007-11-26
Thanks wieman, that gives me somewhere to start, but all these examples seem to show how to start a new, independent session on a computer by remote. What I really need to be able to due is take control of a users existing session while having the session display on both the remote machine and the local machine. This idea here is to be able to demonstrate how to use linux to someone else over the internet. Any advice on how, if possible, to do this?

---

### Post by deamon_knight on 2007-11-26
Also, some of this seems out of data. For example: it directs you to edit /etc/X11/gdm/gdm.conf, but I have no such directory /gdm/ or file. I'm using xubuntu 7.10.

---

### Post by Wharf Rat on 2007-11-26
deamon_knight,
I am no pro here but I think you will need a couple of items to set up the remote link.

1. You (the controlling PC, also known as the client) will need to be able to find your relative's PC on the internet.  Since I doubt they will have a fixed IP address you should consider getting a domain from Dyndns. They provide a home for PCs using dynamic IP addresses. 

This way you can find a route and connect to the remote PC.

2. Ubuntu 7.10 supplies a VNC client and server called Remote Desktop.  The Client is called Terminal Server Client. You either enter the IP address or domain name for the remote (server) PC.  On the server PC you set up a password for your (the client) to use. 

Upon logging in, the server desktop has a Pop-Up on the desktop warning of some remotely  accessing the machine.  This is NOT the same as you logging into the machine for a session.  You are logging into the existing session that your relative is using. You can monitor and control their desktop. I am pretty sure this will run on any of the Ubuntu packages. In fact, I think it can be cross-platform but I have not verified it yet.


You mentioned using Xubuntu.  Have you tried Gnome?  After setting up a couple of Ubuntu machines at work for general internet access. I find that most people can get around in Gnome with the least amount of effort/knowledge.  The base package isn't very pretty but it sure seems functional.

---

### Post by superwad on 2007-11-26
I use the standard install of x11vnc.  If they are logged into only one user, then you simply SSH into their computer, and log in as the user they are.  For instance:

```
ssh joe@1.1.1.1
```
(where joe is the user they are logged in as, and 1.1.1.1 is either the IP or the hostname they have)

Next, you would type:

```
x11vnc -display :0
```

This will start up a VNC session attached to the first desktop session, which should be the one they're using.  You can play around with the options to enable password-protected connections.  If :0 doesn't work, you may need to use :1.

Then you simply open up your VNC client (TightVNC, RealVNC, WinVNC, whatever), and type in the same address after the '@', authenticate if necessary, and you're seeing their desktop in real time.

The port you need to open for the default install is 5900 (I also open up 5901 just to be safe), only if they're using a router.

Hopefully this should work for you.

---

### Post by deamon_knight on 2007-11-28
Thanks for the advice guys. Warf Rat I'm using Xubuntu because Xfce is supposed to have a low system footprint. This is a 600 MHz celeron with 384 MB ram. Its running snappily enough for just using Thunderbird/Skype/firefox so it should get the job done. I'm still new to linux so i suppose there may be better distros but I'm really only familiar with the ubuntu family. Also, my experince with broadband connections has been that you get a fixed IP (or one that only changes infrequently). I'll be installing a router to be safe, so I should be able to bookmark the routers control page if the user has to access it and read off the IP address.

Superwad, what packages do I have to look for to install x11vnc? I suppose I will need this on both the client (my computer) and the server (the users computer),. Having done this, what configuration will I need to do to make it work? None? Just leaver the X11vnc server running, forward the correct port to users computer, type SSH [email]user@1.1.1.ip[/email]; then x11vnc -display :0, then point the Ubuntu remote client to the users IP again and bingo? Almost sounds too easy!

---

### Post by deamon_knight on 2007-12-05
Update, google brought up X11vnc's homepage easy and configuration was painless.  Works just as I needed, thanks!

---

