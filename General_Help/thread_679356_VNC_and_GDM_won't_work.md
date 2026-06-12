---
title: "VNC and GDM won't work"
date: 2008-01-26
forum: General Help
---

### Post by jacensolo on 2008-01-26
I'm trying to connect to my desktop and log in through the gdm via vnc and xinetd. I followed the following tutorial step by step: [http://www.fedoraforum.org/forum/archive/index.php/t-1606.html](http://www.fedoraforum.org/forum/archive/index.php/t-1606.html)

but when I try to connect this is what I get ```
Ccon:   connected to host 192.168.0.2 port 5901
main:    End of stream
```

Nothing else shows up. When I try to do a regular VNC with ubuntu's regular VNC it works. I can't get to the GDM though. 

I would post the VNC logs, but I can't find them :(. 

Thanks for any help!

---

### Post by Rocket2DMn on 2008-01-26
You're following a tutorial that is a few years old and is not geared toward Ubuntu - the fedora setup is a little different.  Here are a few links to help you setup VNC on Ubuntu, though you may want to undo what you did with the fedora tutorial.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
or
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by jacensolo on 2008-01-26
> **Rocket2DMn said:**
> You're following a tutorial that is a few years old and is not geared toward Ubuntu - the fedora setup is a little different.  Here are a few links to help you setup VNC on Ubuntu, though you may want to undo what you did with the fedora tutorial.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
or
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

The part I need is the same in the first link as is the tutorial I was following, I looked at every step. I have no idea what the 2nd link is. I'm looking into it.

---

### Post by Rocket2DMn on 2008-01-26
> **jacensolo said:**
> The part I need is the same in the first link as is the tutorial I was following, I looked at every step. I have no idea what the 2nd link is. I'm looking into it.

I don't really understand what you're saying here.  You should probably install tightvncserver as in the tutorial in the first link I gave you.  You can ignore the second link.

---

### Post by jacensolo on 2008-01-26
> **Rocket2DMn said:**
> I don't really understand what you're saying here.  You should probably install tightvncserver as in the tutorial in the first link I gave you.  You can ignore the second link.

I'm saying that the two tutorials are one of the same. I already did all those steps.

---

### Post by Rocket2DMn on 2008-01-26
Errrr, the fedora tutorial and the Ubuntu tutorial are not the same thing.
So when you say it works with Ubuntu's regular VNC, do you mean when you load vncviewer it works or when you run the built in vnc server it works?
Is the server a fedora computer or an ubuntu computer?
If it's an ubuntu computer, you should undo what you did with the fedora tutorial.

---

### Post by jacensolo on 2008-01-27
Okay, I just reformatted and am starting over with a fresh install of gutsy. I followed this guide: [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Now I'm getting: ```
VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sun Jan 27 09:33:34 2008
 CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)

```

Even when I connect to the same machine (localhost.) I also have a laptop that is connected to the host via an Ethernet cable and it's getting the problem. Any suggestions?

---

### Post by Rocket2DMn on 2008-01-27
It's obviously not a port forwarding problem in your router or anythintg, but it still might be iptables (linux's built in firewall).  Here is a link that talks all about iptables, you may want to download and install "firestarter" as a good GUI to edit iptables.  I've never used it myself, but people say it's good, so it's worth a shot - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
Can you please post a screenshot of exactly what appears?
Also, try accessing the server on port 5901 instead of 1 and see what happens.

---

### Post by jacensolo on 2008-01-27
> **Rocket2DMn said:**
> It's obviously not a port forwarding problem in your router or anythintg, but it still might be iptables (linux's built in firewall).  Here is a link that talks all about iptables, you may want to download and install "firestarter" as a good GUI to edit iptables.  I've never used it myself, but people say it's good, so it's worth a shot - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
Can you please post a screenshot of exactly what appears?
Also, try accessing the server on port 5901 instead of 1 and see what happens.

I have firestarter on my laptop so I know what you're talking about. I'll try it tomorrow.

---

### Post by jacensolo on 2008-01-28
Here's a screen shot:
[[IMG]http://img299.imageshack.us/img299/7483/screenshot2fm0.th.png[/IMG]](http://img299.imageshack.us/my.php?image=screenshot2fm0.png)

And my firestarter settings: [[IMG]http://img295.imageshack.us/img295/6307/screenshotgf2.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshotgf2.png)

Also, it says to apply policy, but rest assured that I did.

---

### Post by Rocket2DMn on 2008-01-28
I'm pretty much at a loss now.  It might be about time to post a bug report on launchpad - [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
Assuming you've followed the directions from Ubuntu's help site correctly, you should be in business, but since you're not, a bug report should be filed.  Sounds like a server end problem to me, so you should file the bug with vncserver instead of viewer.
I'm sorry I wasn't able to help fix your problem :(

---

### Post by jacensolo on 2008-01-28
> **Rocket2DMn said:**
> I'm pretty much at a loss now.  It might be about time to post a bug report on launchpad - [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
Assuming you've followed the directions from Ubuntu's help site correctly, you should be in business, but since you're not, a bug report should be filed.  Sounds like a server end problem to me, so you should file the bug with vncserver instead of viewer.
I'm sorry I wasn't able to help fix your problem :(

Thank you, I really appreciate your effort. I'm just suprised you're the only one who tried to help.

---

### Post by jacensolo on 2008-01-30
Okay, now I got XDMCP working after a reformat. I can't get XDMCP to work through VNC though. I guess I can live with it. Maybe there is a XDMCP client for windows.

---

### Post by moopere on 2008-02-16
> **jacensolo said:**
> Okay, now I got XDMCP working after a reformat. I can't get XDMCP to work through VNC though. I guess I can live with it. Maybe there is a XDMCP client for windows.

Cygwin will probably do what you want under Windows..ie; give you a local display of your remote linux machine.

Have a snoop at this:

[http://cygwin.com/](http://cygwin.com/)

Cheers,
Craig

---

