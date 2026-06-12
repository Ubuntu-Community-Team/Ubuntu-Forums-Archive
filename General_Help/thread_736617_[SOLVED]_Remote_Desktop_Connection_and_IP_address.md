---
title: "[SOLVED] Remote Desktop Connection and IP address"
date: 2008-03-26
forum: General Help
---

### Post by cybo on 2008-03-26
I want to use an RDC from a Windows machine (work) to connect to home Linux over the internet. I looked up how to do that in windows and it says I need an IP address of my computer. Can anyone tell me how to find out an IP address of my computer and it would be nice to know what IP is? I'm new to linux and computer world overall but really eager to learn.

Thank you

---

### Post by wormser on 2008-03-26
An easy way to get your address is here [http://www.whatismyip.com/](http://www.whatismyip.com/).  You are also going to [port forward]("http://portforward.com/routers.htm") your router.  I recommend using putty to ssh via VNC to the Ubuntu box.  Just search the forum or the net for a HowTo.

---

### Post by PilotJLR on 2008-03-26
Yeah, I second that! Use an ssh port forward to vnc... it would not be safe to open vnc up unencrypted. ssh is the safe bet.

---

### Post by cybo on 2008-03-27
I still can't connect to my computer at home.[Here]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html") is what I'm doing. Will I have to approve my connection every time I connect from one my work computer to my home computer? That kind of defeats the purpose of RDC.
I'm not using port forwarding yet. I just wanted to find out if I can connect to my comptuer at home. 

Can anyone help?

---

### Post by yota on 2008-03-27
You can setup a password instead of the confirmation dialog.

Go to system/preferences/remote desktop and select to ask for a password (and de-select "ask confirmation")

note: I've translated from italian, so the menu names can be inaccurate.

Hope this helps

---

### Post by cybo on 2008-03-27
Thnx. I'll try it at home and see what happens. Currently at work so there won't be an answer until 10 hrs later.

---

### Post by cybo on 2008-03-27
> **wormser said:**
> An easy way to get your address is here [http://www.whatismyip.com/](http://www.whatismyip.com/).  You are also going to [port forward]("http://portforward.com/routers.htm") your router.  I recommend using putty to ssh via VNC to the Ubuntu box.  Just search the forum or the net for a HowTo.

I'm not using a router. I have a cable modem at my place. How do I port forward it? If I can't is there a way to encrypt my VNC connection?

Thnx

---

### Post by wormser on 2008-03-27
> **cybo said:**
> I'm not using a router. I have a cable modem at my place. How do I port forward it? If I can't is there a way to encrypt my VNC connection?

Thnx

Go an buy a router.  They are cheap and greatly increase your security.  Cable modems do not need to be port forwarded.  You need to set up sshd on your system.  Then tunnel VNC through it.  I found a tutorial for you:  [http://ubuntuforums.org/showthread.php?t=383053&highlight=vnc+ssh](http://ubuntuforums.org/showthread.php?t=383053&highlight=vnc+ssh).  You can skip the keys part of the tutorial if you want to use passwords instead.

---

