---
title: "Use Windows RDP to connect to Ubuntu Edgy Machine?"
date: 2006-11-01
forum: General Help
---

### Post by TwiceOver on 2006-11-01
I was wondering if anyone knew of a RDP server program that I could run on Edgy and use Windows RDP Client to connect to it.

I've used VNC in the past, and have been less than pleased with it.  Also almost every Windows machine I touch has the RDP Client on it, so it would be nice to be able to use something that is already built into Windows.

---

### Post by Joe_CoT on 2006-11-02
You can set up remote desktop in gnome at System -> Preferences -> Remote Desktop. That uses RDP

---

### Post by jasutton on 2006-11-02
I don't believe that's correct.  The Remote Desktop dialog in System->Preferences is for setting up a VNC server, not RDP.

For an actual RDP server for Linux, you may want to look here:

[http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/)

---

### Post by jasutton on 2006-11-02
I just downloaded and compiled xrdp from the link I posted above, and found that I needed libpam0g-dev installed for it to compile correctly.  I'm not sure exactly how/if it works yet, but I'm going to experiment a little with it.

---

### Post by Sunon on 2006-11-16
I got xrdp to work in Edgy (a brand new install) after a couple of days of fiddling with it.  Here are the steps I took:

-Install vnc4server, vnc4-common from synaptic (you need to have the universe repository enabled for this)

-to get vnc to work properly I had to symlink my fonts path, I don't recall the path it was looking for but to test just run "Xvnc :1" and it should give a font error.  I found my font path by running "locate fonts"  of course it gave a long list but it was pretty easy to see where they were.  The issue is that vnc was looking in fonts/X11/...  and they were actually in X11/fonts.  So I created an X11 directory in fonts and then ran "ln -s /real/font/path/ /path/to/new/X11/dir"  even after linking the fonts path vnc gave a warning or two but it ran ok.

-Install libpam0g-dev from synaptic

-downloaded the latest version of xrdp from the project homepage

-compile/install xrdp

-edit the /usr/local/xrdp/startwm.sh script
  -I took out all of the kde lines and then changed the gnome section to launch dbus-launch gnome-session instead of just gnome-session

to run xrpd I used the control script: xrpd_control start

I wish I could say that I ran all of the steps in this order, it would have saved me a lot of time.  I didn't realize that xrdp needed a seperate vnc to work.  I thought it came with its own implementation.  So I kept getting errors in the sesman.log like "error starting window manager" or "session terminated for user xxx"  what was happening was it was trying to launch kde at first (I don't have kde) and also it was trying to launch Xvnc and Xvnc was failing because of the font problem, although from the sesman errors you would have no idea of this.

After all of this I was able to connect from my XP box through remote desktop and it works perfectly.

Hope this helps all of you out there trying to get Xrdp to work in ubuntu.

---

### Post by kiranlightpaw on 2007-01-01
Greetings!

I'd like to expand on the excellent previous post with a little bit more information and a step-by-step that I just went through to install and get xrdp up and working.

1. Install the following packages from Synaptic (you'll need to turn on the Universe repository):
- vnc4server
- vnc4-common
- libpam0g-dev
- libssl-dev (it won't build without this)

2. Fetch xrdp sources from [http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/). Un-gzip and tar it into a directory.

3. SU to root, CD to the directory where the xrdp sources you just got are, then:

```

make
make install
```

4. Fix the font problem between X11 that ships with Ubuntu and Xvnc. I did this by: 

```
ln -s /usr/share/fonts/X11 /usr/share/X11/fonts
```

5. Edit the startwm.sh script in /usr/local/xrdp/startwm.sh. I just nuked the whole thing and created a new startwm.sh with the following in it:

```

#!/bin/sh
dbus-launch gnome-session
```

6. Start xrdp

```
./xrdp_control.sh start
```

7. Connect to it with the RDP client of your choice. It seems to be working with WinXP's RDP client, but I really wanna test it with some winterms. :P

---

### Post by rappazzo on 2007-01-07
After having xrdp working for a long time, my edgy (fresh install) system decided that vnc4server package needed an upgrade.  Ever since that upgrade, xrdp has not been working.  I can log into sesman, but when it tries to connect to (presumably) Xvnc, it says error connecting.

I tried to uninstall and reinstall everything from scratch, but still the same problem persists.  Therefore, I a guessing it is a configuration problem of some sort.  If anyone can help, that would be great.  

Is anyone else having this problem too?

---

### Post by Sunon on 2007-01-08
I just got the problem as well, I'm currently working on fixing the issue.  I'll post any information I can if I find out what the issue is.

---

### Post by Sunon on 2007-01-09
looks like the issue is with vnc4server.  Some people have had luck with just installing the previous version of vnc4server.  I'll keep looking into the issue, but I imagine there will be a bug fix of some sort soon.

---

### Post by Sunon on 2007-01-09
Ok, so I just changed my startwm.sh script to start blackbox instead of gnome-session and I got a session to work with no problems.  I think the problem is a clash with vnc4server and gnome.  I have read some posts just about the new vnc4server having issues with gnome and my results seem to mirror that experience.

Edit:
Here is the link to the bug...
[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282)

Downgrade for now and wait for a fix I guess...
run:
apt-get install vnc4server=4.1.1+xorg1.0.2-0ubuntu1

---

### Post by rappazzo on 2007-01-09
That fixed it.  Ok, great.  Thankfully I didn't do anything too crazy to mess up my setup :) 
Your help is much appreciated.  I guess I will subscribe to that bug, and not upgrade until it is fixed.  Thanks again.

---

### Post by rappazzo on 2007-01-09
So...as long as we are fixing/discussing xrdp...Maybe you can help me figure out a few oddities that I think it has.  I don't know if it is something in the underlying xrdp server, or if it is just a setup issue that I have.

First thing, is that if I don't have a logged in session at the computer itself, I get Xauthorization issues.  As a specific example, if I connect and try to run synaptic package manager, I get a dialog box that says, "Failed to run /usr/sbin/synaptic as user root.  Unable to copy the user's Xauthorization file."

Secondly, normally when I am logged in at the computer, on the desktop, anything that is mounted in the /media/ directory automaticly show up.  BUT, when I rdp, those links(?) are not present.  

So, is there something that I can do to fix these to be more desirable?  These are minor details, that I can live with, and work around, so If no one has any ideas, it isn't a big deal.

Thanks.

---

### Post by Sunon on 2007-01-10
> First thing, is that if I don't have a logged in session at the computer itself, I get Xauthorization issues. As a specific example, if I connect and try to run synaptic package manager, I get a dialog box that says, "Failed to run /usr/sbin/synaptic as user root. Unable to copy the user's Xauthorization file."

I have seen this issue myself, In fact I run my linux box totally headless (I remote in for everything).  And it is an annoyance for me too.  What I usually end up doing is opening an xterm box and run synaptic either doing a sudo command or just as superuser (su command).  I'll see if I can dig anything up on this.

Edit:
Ok I think I figured out the first issue... Here is how I fixed it:
Copy the root .Xauthority file to your user's home.
sudo cp /root/.Xauthority /home/username/
sudo chown username:group /home/username/.Xauthority

my group was the same as my username

---

### Post by tatoosh on 2007-02-19
Hi there,

i have two problems with remote connection:
1st one:

i folowed the instruction to get xrdp to run.
my os is kubuntu (kde).

when i connect to my kubuntu from windows vista mstsc i only get black screen and a mousepointer.

any ideas ?
thx alot.
-------------------------------------------------------------------
2nd one:
also my vncserver doesn't work. this is my errormessage:

Couldn't start Xvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xvnc process.

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
19/02/07 13:51:39 Xvnc version 3.3.tight1.2.9
19/02/07 13:51:39 Copyright (C) 1999 AT&T Laboratories Cambridge.
19/02/07 13:51:39 Copyright (C) 2000-2002 Constantin Kaplinsky.
19/02/07 13:51:39 All Rights Reserved.
19/02/07 13:51:39 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
19/02/07 13:51:39 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
19/02/07 13:51:39 Desktop name 'X' (tatoosh-laptop:1)
19/02/07 13:51:39 Protocol version supported 3.3
19/02/07 13:51:39 Listening for VNC connections on TCP port 5901
19/02/07 13:51:39 Listening for HTTP connections on TCP port 5801
19/02/07 13:51:39   URL [http://tatoosh-laptop:5801](http://tatoosh-laptop:5801)
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
19/02/07 13:51:40 Xvnc version 3.3.tight1.2.9
19/02/07 13:51:40 Copyright (C) 1999 AT&T Laboratories Cambridge.
19/02/07 13:51:40 Copyright (C) 2000-2002 Constantin Kaplinsky.
19/02/07 13:51:40 All Rights Reserved.
19/02/07 13:51:40 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
19/02/07 13:51:40 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
19/02/07 13:51:40 Desktop name 'X' (tatoosh-laptop:1)
19/02/07 13:51:40 Protocol version supported 3.3
19/02/07 13:51:40 Listening for VNC connections on TCP port 5901
19/02/07 13:51:40 Listening for HTTP connections on TCP port 5801
19/02/07 13:51:40   URL [http://tatoosh-laptop:5801](http://tatoosh-laptop:5801)
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring

Fatal server error:
could not open default font 'fixed'

---

### Post by Sunon on 2007-02-21
tatoosh,
It would seem that your problems go hand in hand.  When I had issues with my VNC server, Xrdp wouldn't allow a connection at all.  But it seems in your case, it allows a connection but VNC is crashing because it cannot find the font path.  All Xrdp does is take the commands from a regular terminal services client and hands them on to a VNC server (other processing may take place, but that's the basic idea).  What you need to do is fix your font path, and the easiest way for me was to create a link.  Your VNC server wants your fonts to be located in this path: /usr/X11R6/lib/X11/fonts/ and they are actually somewhere else.  I don't know where this would be for you because you are running kubuntu (it is probably the same because both need X11 to run, but I don't know for certain).  I am running the regular ubuntu which uses the GNOME desktop.  When you find out where your fonts are just create the path tree for /usr/X11R6/lib/X11/ and use the link command like I posted earlier but point it to where YOUR fonts are.  Also you need to check to see if the /usr/local/xrdp/startwm.sh script is trying to use the KDE desktop or GNOME.  For your system you need it to start KDE (my previous instructions were for the default GNOME)

---

### Post by razorsmile on 2007-03-07
I'm about to try and set this up to access my home machine from work and wanted to know if there's anything I should know...my home machine is one amongst three on a home network (two ubuntu and a windows media center - my ubuntu is hardwired into the router, the othe rtwo machines wireless connections.  The router is the wan interface so using windows RDP remote connection to establish a remote to my Ubuntu box implies me using the IP for the home network but this is (in effect) my router...do I have to add some way of forwarding the RDP request to the right box within my LAN - it seems logical that I would have to but no idea how that would work...any thoughts?

:-k

---

### Post by Sunon on 2007-03-07
razorsmile,
There are 2 main options to consider.  First is to put your ubuntu box on the router's DMZ (more on that later), Second is to portforward the RDP port (3389) to your ubuntu box.  I personally went with option 2 because I only forward the ports that I want outside access to.  This way you are still using NAT (network address translation, ie not a real world ip) and you get the benefits of being less likely to be a victim of an attack of some service on some random port.  Option 1 puts your computer right out in the open and anybody can hit whatever port they want to.  In this scenario I would highly recommend you use a good firewall and strong passwords.  Option 2 can still benefit from having a firewall but generally NAT is good enough for my purposes.

---

### Post by razorsmile on 2007-03-10
thanks for that and I'll go with the port forarding to begin with and see how that works, though it looks like it will be a couple of weeks before I set it up now...though I will do an initial attempt on monday...

---

### Post by holst on 2007-04-09
I have a problem with input locale. I want to use Swedish keyboard (more precisely the "åäö" characters). I start the server as xrdp_control.sh start and connect using rdesktop -k sv remotehost. No error appears in the console. However the input locale is clearly not Swedish... :-(

Any input on this? Have anyone successfully changed input using rdesktop -k option?

Thanks / Henrik Holst

---

### Post by holst on 2007-08-06
(I am answering my own question)

The support for Swedish input locale (and more) was not in the 0.4.0 release of Xrdp. However, you can get the code from CVS and you will have the support for Swedish.

Xrdp is a very nice program even now in it's early state. It has been included into Debian repos. I think, in version 0.5.0 (or maybe 0.6.0) Xrdp will have reached "commercial grade" quality. 

Watch out Microsoft! :grin:

/holst

---

### Post by HermanAB on 2007-08-07
BTW, I have found that it is generally less trouble to install PuTTY on Windows and use that to connect to Linux using SSH.  Turn X forwarding on  and you can then log in and run anything directly without the slowdown and overhead of a complete desktop.

---

