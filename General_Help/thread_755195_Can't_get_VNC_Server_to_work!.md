---
title: "Can't get VNC Server to work!"
date: 2008-04-14
forum: General Help
---

### Post by mistaWAC on 2008-04-14
Okay, I've spent about two hours total looking for information on how to setup a VNC server on my Ubuntu desktop at my house and I have had no luck whatsoever.  Every link I click seems to lead me to the same tutorial or walkthrough.

I've enabled the Remote Desktop thing on the computer and given it a password.
I've opened ports 5900 and 5800.

I can't connect.  WTF?!  I tried the Java thing and I got to the login thing through my browser but after I typed in my username/password it said it couldn't connect.

ANY help?!

---

### Post by artblakey on 2008-04-14
Are you trying to set up the VNC server so you can use the computer from another computer on the same network, or accross the internet?

If it's the latter you'll probably need to configure your router, as well as your firewall, to allow access on certain ports, I'm not sure whether you meant that when you said you'd opened the ports.

One other thing... as far as I'm aware to access a computer via VNC, the user your loggging on as has to already be logged on locally at the machine your trying to access... if that makes any sense. So if you log on on your Ubuntu box then leave it running, VNC will allow you to control the desktop from another computer.

---

### Post by mistaWAC on 2008-04-14
The computer is always logged in as my user and it is across the internet.  I did open the ports some of the tutorials said to open.

---

### Post by bodhi.zazen on 2008-04-14
We need more information.

What version of Ubuntu ?

java ? are you talking about the default vncserver (vino) or vncserver (java server) ?

Is the server running ? Try connecting from Ubuntu to ubuntu, localhost.

Firewall ?

When you say "opened ports" are you saying you have a router and have forwarded the ports ?

See this link : [uwiki]VNC[/uwiki]

---

