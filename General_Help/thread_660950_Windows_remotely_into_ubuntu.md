---
title: "Windows remotely into ubuntu"
date: 2008-01-07
forum: General Help
---

### Post by Bailey321 on 2008-01-07
Ive searched and noticed countless threads about this but honestly none are helpin my situation. Im a bit of a begginer here and this is my last resort before i forget ubuntu ever existed ;( hopefully somebody can help me out.

Ive installed ubuntu 6.06 on my server (countless times) and basically i want to be able to remote into it using xp. I have found countless guides and followed them all to the best of my limited ability. The only one that works is the freenx server option but in order for me to connect i HAVE to use the client V1.5 the newest version v3.* will not connect, using version1.5 causes problems, altho it will let me resume- upon resuming it totally crashes and will not let me resume more then once. I have also tried vncviewer enalbing the option via the ubuntu desktop (which is only available to me if i install freenx) but all i get is a white blank screen even tho it connects fine.

Ive spent all night tryin to do this, please can sombody give me some sort of resumable solution that does not require me to visit the desktop to set it up first because obviously im doin all this through putty.

---

### Post by tech9 on 2008-01-07
try RealVNC that's what I use... it works flawlessly, just make sure that you enable remote logon under Remote Desktop System>Preferences>Remote Desktop

---

### Post by Bailey321 on 2008-01-07
Yup i tried that thats the one that connects fine but just gives a white blank screen, the mouse actually moves around the desktop i just cant see it.

---

### Post by tech9 on 2008-01-07
it could be that vnc is having a hard time picking up your video card... what kind of card do you have?

---

### Post by stalker145 on 2008-01-07
> **Bailey321 said:**
> Ive searched and noticed countless threads about this but honestly none are helpin my situation. Im a bit of a begginer here and this is my last resort before i forget ubuntu ever existed ;( hopefully somebody can help me out.

Ive installed ubuntu 6.06 on my server (countless times) and basically i want to be able to remote into it using xp. I have found countless guides and followed them all to the best of my limited ability. The only one that works is the freenx server option but in order for me to connect i HAVE to use the client V1.5 the newest version v3.* will not connect, using version1.5 causes problems, altho it will let me resume- upon resuming it totally crashes and will not let me resume more then once. I have also tried vncviewer enalbing the option via the ubuntu desktop (which is only available to me if i install freenx) but all i get is a white blank screen even tho it connects fine.

Ive spent all night tryin to do this, please can sombody give me some sort of resumable solution that does not require me to visit the desktop to set it up first because obviously im doin all this through putty.

Relax, dude. It'll be OK. 

Have you tried NoMachine? (i've heard it's similar to FreeNX (which I've never used). The NoMachine server requires no setup and you should be able to install it through SSH, as you say you're using.

Also, there's no reason that you are required to install FreeNX just to use VNC (unless, of course, you are talking about tunneling VNC through SSH which NoMachine can do, as well).

Simple SSH is probably the most efficient way to do business, but if you're like me, a GUI is preferable (I don't know a whole lot of CLI commands). 

Since this is your first cry for help, just try to let us work with you and try not to be so threatening... it really doesn't help around here in getting support.

Let us know if there's anything else that we can do to help.

---

### Post by Bailey321 on 2008-01-07
@ tech i remember tryin this on my old machine with a different GC and had the exact same problem, so i doubt its the video card but here it is anyway......Leadtek WinFast GeForce 7600 GS 256MB DDR2 PCI-E 

@ stalker - Sorry if i came across as such, just a lil frustrated thats all..../me not threating anyone ;(

I to need a GUI as the command line is not my fortee. This Nomachine works as a server lookin from google but the Q is how to install this via putty ?

Like this.....maybe?

wget [http://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-78_i386.deb](http://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-78_i386.deb)
wget [http://64.34.161.181/download/3.0.0/Linux/nxnode_3.0.0-83_i386.deb](http://64.34.161.181/download/3.0.0/Linux/nxnode_3.0.0-83_i386.deb)
wget [http://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-69_i386.deb](http://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-69_i386.deb)
sudo dpkg -i nxclient_3.0.0-78_i386.deb
sudo dpkg -i nxnode_3.0.0-83_i386.deb
sudo dpkg -i nxserver_3.0.0-69_i386.deb

---

### Post by tech9 on 2008-01-07
> **Bailey321 said:**
> @ tech i remember tryin this on my old machine with a different GC and had the exact same problem, so i doubt its the video card but here it is anyway......Leadtek WinFast GeForce 7600 GS 256MB DDR2 PCI-E 

@ stalker - Sorry if i came across as such, just a lil frustrated thats all..../me not threating anyone ;(

I to need a GUI as the command line is not my fortee. This Nomachine works as a server lookin from google but the Q is how to install this via putty ?

Like this.....maybe?

wget [http://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-78_i386.deb](http://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-78_i386.deb)
wget [http://64.34.161.181/download/3.0.0/Linux/nxnode_3.0.0-83_i386.deb](http://64.34.161.181/download/3.0.0/Linux/nxnode_3.0.0-83_i386.deb)
wget [http://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-69_i386.deb](http://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-69_i386.deb)
sudo dpkg -i nxclient_3.0.0-78_i386.deb
sudo dpkg -i nxnode_3.0.0-83_i386.deb
sudo dpkg -i nxserver_3.0.0-69_i386.deb


ok, well we know it isn't the video card then, + that card should work just fine with RealVNC.

maybe try stalker suggestion with NoMachine

---

### Post by stalker145 on 2008-01-07
> **Bailey321 said:**
> @ tech i remember tryin this on my old machine with a different GC and had the exact same problem, so i doubt its the video card but here it is anyway......Leadtek WinFast GeForce 7600 GS 256MB DDR2 PCI-E 

@ stalker - Sorry if i came across as such, just a lil frustrated thats all..../me not threating anyone ;(

I to need a GUI as the command line is not my fortee. This Nomachine works as a server lookin from google but the Q is how to install this via putty ?

Like this.....maybe?

wget [http://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-78_i386.deb](http://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-78_i386.deb)
wget [http://64.34.161.181/download/3.0.0/Linux/nxnode_3.0.0-83_i386.deb](http://64.34.161.181/download/3.0.0/Linux/nxnode_3.0.0-83_i386.deb)
wget [http://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-69_i386.deb](http://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-69_i386.deb)
sudo dpkg -i nxclient_3.0.0-78_i386.deb
sudo dpkg -i nxnode_3.0.0-83_i386.deb
sudo dpkg -i nxserver_3.0.0-69_i386.deb

That *should* work out fine doing the above. I don't recall, but I *think* the order is actually reversed... check the web site, though. It's been a while since I've installed this app and I can't access the site since I'm at work and they want us to work ;)

What I meant by my previous comment about threatening: we get a lot of folks around here who get understandably frustrated. Their frustration generally leads to a "fix this or I'm out'ta here" thread. Sorry I wasn't more specific.

But, seriously, let us know if this solution works out for you. If it doesn't, I'm sure there are others...

---

### Post by Bailey321 on 2008-01-07
I understand sir, but im determind thats just frustration talkin, I will never quit baby! :)

Alrighty then im a google this like mad and report back on wether i succeed!

---

### Post by Bailey321 on 2008-01-07
root@sd-4209:~# sudo dpkg -i nxserver_2.1.0-9_i386.deb
Selecting previously deselected package nxserver.
(Reading database ... 87913 files and directories currently installed.)
Unpacking nxserver (from nxserver_2.1.0-9_i386.deb) ...
Setting up nxserver (2.1.0-9) ...
NX> 704 ERROR: Cannot add user: nx. User: nx already exists.
NX> 704 ERROR: Please try to fix the problem by reinstalling the server.
dpkg: error processing nxserver (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver

This was the error i got on the last part of the installation, any ideas what it means?

OK just tried it and its connecting but seesion startup is failing this is the error report..

NX> 148 Server capacity: not reached for user: root
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --media="0" --session="session1" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/gb" --screeninfo="1280x994x16+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: sd-4209-1000-FF6FFCFBFA135933EC0DE23DB24128ED
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 4d0681d13e7eb8998f2759e911affd73
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 4d0681d13e7eb8998f2759e911affd73
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/lib/nx/nxserver: line 891:  8124 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
NX> 280 Exiting on signal: 15

---

### Post by stalker145 on 2008-01-07
> **Bailey321 said:**
> Setting up nxserver (2.1.0-9) ...
NX> 704 ERROR: **Cannot add user: nx. User: nx already exists.**
NX> 704 ERROR: Please try to fix the problem by reinstalling the server.

Did you try reinstalling and receive the same problem? If so, see below.

This is the only thing that really jumps out at me. Check in your User Management and delete any users named nx. Then try reinstalling.

Sounds good, anyway ;)

---

### Post by cdenley on 2008-01-07
I've never used nxserver, but you should be able to use VNC. Are you always logged on locally on the server? I'll assume you aren't always logged in, and that you're using gnome.

from the server, through ssh:
```

sudo apt-get install vnc4server
echo \#\!/bin/sh>~/.vnc/xstartup
echo [ -x /etc/vnc/xstartup ] \&\& exec /etc/vnc/xstartup>>~/.vnc/xstartup
echo [ -r $HOME/.Xresources ] \&\& xrdb $HOME/.Xresources>>~/.vnc/xstartup
echo xsetroot -solid grey>>~/.vnc/xstartup
echo vncconfig -iconic \&>>~/.vnc/xstartup
echo exec gnome-session \&>>~/.vnc/xstartup
vncserver

```

From the client, connect to port 5901, and you will have a gnome session. If you're logged in on the server locally, you will probably have an empty, grey X window. I've tested this on gutsy, but it should work the same on dapper.

---

### Post by Bailey321 on 2008-01-07
Ok i now have it running how i want :)

Basically even tho the server installation showed that error it did actually install and run. As for the client i can only get nxclient v1.5 to work but what ive managed to do is  make my sessions resumable which is all i was after.

Thanks to all you good fellows for the fast responses :D

---

### Post by kriot on 2008-01-08
Hi All,

I'm trying to set up the same thing however my problem is that i'm not looking at the ubuntu desktop to begin with. I'm trying to do this via terminal window. Is there a config file somewhere where I can enable remote control?

KC

---

