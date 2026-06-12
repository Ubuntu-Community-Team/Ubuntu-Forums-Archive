---
title: "Remote Desktop to Xubuntu"
date: 2006-11-09
forum: General Help
---

### Post by abrarey on 2006-11-09
Hi I just installed xubuntu and I think is great for slow pcs and for servers.
I want to know how to enable remote desktop so I can connect from any machine and use the GUI. Now I'm using only the terminal via SSH. I've been looking for the remote desktop option that is on ubuntu but i can't find it here.
Any suggestion.

---

### Post by Choad on 2006-11-09
> **abrarey said:**
> Hi I just installed xubuntu and I think is great for slow pcs and for servers.
I want to know how to enable remote desktop so I can connect from any machine and use the GUI. Now I'm using only the terminal via SSH. I've been looking for the remote desktop option that is on ubuntu but i can't find it here.
Any suggestion.
i think "sudo apt-get install vino xvnc4viewer" will do the trick

---

### Post by abrarey on 2006-11-09
OK, yes I've installed those apps already, but i need to know how to configure the vnc server because i don't see in the menu the option to configure.

---

### Post by abrarey on 2006-11-09
Ok I Found it i just type in console vino-preferences.
Thanks anyway

---

### Post by srf21c on 2006-11-11
Did you ever get this working?  I have been unable to get the vino server to launch under Xubuntu 6.10.  

I filed a bug report here: [https://launchpad.net/distros/ubuntu/+source/xfce/+bug/71335](https://launchpad.net/distros/ubuntu/+source/xfce/+bug/71335)

One of the developers told me that it was a problem with xfce failing to launch the vino server.  (the vino server is usually launched by the gnome session manager, IIRC)

---

### Post by moon2js on 2007-03-30
Anyone by any chance know how to manually start vino? I don't mind ssh'ing in and starting it.

---

### Post by srf21c on 2007-03-30
You could try firing it off remotely by running /usr/lib/vino/vino-server

Not sure if that works unless the remote user is already logged into the desktop however.

Also I was able to get the vino server to launch automatically under Xubuntu 6.10 by plugging the path above into the "autostarted" applet.

---

### Post by Brokenwrist on 2007-04-01
Hi all ^^
Don't know much about vino server, rather I would like you to have a look to [http://www.nomachine.org](http://www.nomachine.org) . I actually use the free NXServer version, it's really fast, SSH-tunneled, and very simple to configure.

Ciao ciao,
BrokenWrist

---

### Post by srf21c on 2007-04-19
Does the FreeNX solution allow someone to share the remote console desktop session with a user who is physically at the machine?  That's original reason why I sought a solution for Vino, so that I can provide remote support for people Ubuntu/Xubuntu.   Last time I configured FreeNX on a box, I was unable to configure it to achieve this functionality.

---

### Post by zeekay on 2007-04-19
I used to have x0vncserver on my former ubuntu intallation. It worked preety decently (even thou it was a beta version at the time), you only needed to set up a password file and let it run. I liked it a lot and used it for a good period of time.

The good thing about it is that it opens your current X Server session, so it works exacly like the original vnc does on windows.

---

