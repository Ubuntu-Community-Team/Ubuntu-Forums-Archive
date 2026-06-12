---
title: "Simple TightVNCServer instructions"
date: 2015-02-15
forum: General Help
---

### Post by FerryGnu on 2015-02-15
Hi, I have been using windows almost since it started, as in win3.1 and now retired and would like to play with Ubuntu. I have used TightVNC on windows for as long as it has existed.

I have installed Ubuntu 14.4 on a Lenovo laptop and it is currently all updating and rebooting.

The laptop keyboard and red0button/mouse thing is terrible to use so I would like to use TightVNCViewer from my win8.1 laptop to access Ubuntu. I have searched and found a few instuctions that apply to much older versions of Ubuntu and I can't seem to get any to work. My win8.1 shows the IP-address of the Ubuntu laptop, but using instructions for starting tightvncserver seem to get it to run on Ubuntu, but not able to connect from win8.1.

Could someone please point me at some step-by-step instructions for activating tightvncserver, or something else that will work TightVNCViewer from win8.1?

Thanks

---

### Post by Doug S on 2015-02-15
Have you looked at [this]("https://help.ubuntu.com/community/VNC/Servers") page? 

From my windows 8.1 computer, I mainly use tightVNC viewer with my VM's, but also use UltraVNC viewer. I don't actually know what VNC server is running, whatever is the default with kvm on my virtual machines host computer.

I have a persistent problem, where sometimes the viewer and the server get out of sync with respect to the keyboard. I have to minimize and then bring back the viewer to get back in sync.

---

### Post by FerryGnu on 2015-02-15
Thanks, I saw that page, but I first need instructions on how to set up TightVNCServer on Ubuntu as the ones I have found so far were for v6 and v12 and neither worked. 

When using the command as instructed, *sudo apt-get install tightvncserver* it would begin OK and download some stuff then say it need things on other drives. I could not find a way to get it working.

OK, I am getting somewhere. I now have TightVNCServer finally installed and running. But when I try to access it from windows using TightVNCViewer, I get the "...the connection was actively refused by..."

A search here for "actively refused" returns nothing.

I really am at the bottom of the Newbie list with Linux, but I do search a lot before asking. :)

---

### Post by steeldriver on 2015-02-15
If you just want to connect to and share the current desktop, then you can use the default vino-server (aka 'Desktop Sharing') instead of installing and running a standalone VNC server such as tightvncserver

---

### Post by FerryGnu on 2015-02-15
Getting further, but still no cigar. Using online instructions (use 192.168.1.33:5901) I can now get the win8 Viewer to open (I assume it is connected) but I get a blank gray screen with nothing in it.

The viewer is connected I believe, as the title-bar is showing "lenovo-u" which I name the install as, but the cursor (a black X) moves within the viewer, but does not move on the Ubuntu.

See what I mean by I need simple steps? LOL

> **steeldriver said:**
> If you just want to connect to and share the current desktop, then you can use the default vino-server

Thanks, but how do I do that? 
I tried
vino
vino-server

but get "command not found"

I can stop the TightVNCServer, but then what?
Will I access it from win with the TightVNCViewer?

OK, just trying this...
[http://www.libregeek.org/2014/04/29/getting-remote-access-work-ubuntu-14-04-vino/](http://www.libregeek.org/2014/04/29/getting-remote-access-work-ubuntu-14-04-vino/)

Will get back here in a few minutes.

---

### Post by steeldriver on 2015-02-15
A plain gray screen (root window) with an X term is the default ~/.vnc/xstartup - if you want something different you will need to configure it with whatever session or window manager/applications you want. If you search this forum for xstartup + my S/N you should find a few previous threads on that. By aware that the fancy 3D desktop sessions tend not to work well (if at all) over VNC

To start vino-server instead type 'Desktop Sharing' in the dash, or vino-preferences in a terminal. By default it will relay the current desktop (screen :0) on port 5900 so you will need to change your vncviewer connection information accordingly.

---

