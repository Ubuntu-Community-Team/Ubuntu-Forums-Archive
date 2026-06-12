---
title: "FreeNX, RDP and Breezy"
date: 2005-10-20
forum: General Help
---

### Post by jtardis on 2005-10-20
Hi,

I've just loaded Breezy (loving it!) and then added FreeNX from the seveas.ubuntulinux.nl repository.

All is good, connects with the NoMachine client without a hitch - works like a dream but....

The only thing I can't seem to do is use the client to connect to my XP machine via RDP. I can run the nxdesktop from the Breezy box no problem am I missing something in the setup? I've enabled ip_forward in /etc/network/options as well.

Any help gratefully received!

---

### Post by bugmenot on 2005-10-20
You can't use FreeNX to connect to your XP box because it doesn't run an NX server. It's running an RDP service to which you connect with the Terminal Server Client from the Applications menu.

(and yeah, you could tunnel an RDP connection through an NX session, but then you would need an NX Server on the other end as well. FreeNX only builds on OS systems, the Windows server is commercial)

---

### Post by jtardis on 2005-10-20
Hi bugmenot, thanks for the quick reply.

Sorry, I don't think I really explained my problem properly there.

[LIST]
[*]When I'm connecting to a Breezy gnome or xfce session from XP PC(1) using the NoMachine client software, all is good.
[*]When I run 'nxdesktop (name of XP box)' from Breezy I can run a RDP session connecting to XP PC(2), again all is good.
[*]When I set the NoMachine client on XP PC(1) to use NX to connect to XP PC(2) via Breezy it authenticates but never seems to start the nxdesktop session and I get this output

NX> 1000 NXNODE - Version 1.4.0-44 OS (GPL)
NX> 700 Session id: Shuttle-1000-BB7C28FD3FC8B03AB66F8CE6DF7CC093
NX> 705 Session display: 1000
NX> 703 Session type: windows
NX> 701 Proxy cookie: 4a03b08e88a85d8b71020da9eafe144f
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 4a03b08e88a85d8b71020da9eafe144f
NX> 704 Session cache: windows
NX> 707 SSL tunneling: 1
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
[/LIST]


I'm using NX for speed because I going via the internet (somethimes on a 56k modem) kind of looks like this....

XP PC(1) - Internet - Breezy NX Server - Local Lan - XP PC(2)

Cheers.

---

### Post by bugmenot on 2005-10-22
[QUOTE=jtardis]

XP PC(1) - Internet - Breezy NX Server - Local Lan - XP PC(2)[/QUOTE]

Yes, that makes more sense. It actually works like that, as I connect to the Win PC in my Lab that way. 

Make sure that you make the nxclient connect to the Box that's running the nxproxy (Breezy PC). The nxproxy then is instructed to connect to the RDP server (XP PC2) and exchange display stuff, which is then tunneled to you (XP PC 1) through NX compression.

So, how to do it? Choose Windows in the Desktop field in the !M Client and and point it to your XP box in Settings.
The nxhost (or server) is of course the Breezy box.
When you get conneciton erorrs maybe you need to make sure that all the needed ports are open. Choosing "use SSL on all traffic" reduces the ports needed over the net to port 22.

If you still have trouble try to see whether getting RDP onto the Breezy box works. So, firts start an NX GNOME session and then use rdesktop (or Terminal Server Client)  on the remote local lan, i.e. as a cascade.

---

### Post by jtardis on 2005-10-24
Got the connection from XP-PC1 -> Breezy no problem, works well, then I can run 'nxdesktop -a16 -f nameofXP-PC2' and get through to the XP-PC2 that way but when I set up the nxclient to do this as you mentioned it authenticates but never gives me the window on the client machine. 

No !M logo on a black screen nothing, just pauses saying 'authentication completed' and then times out with the error I posted below.

I'm using the Seveas breezy debs for FreeNX, you mentioned yours works OK, did you compile the binaries yourself or get the debs from somewhere else?

Thanks again.

---

### Post by bugmenot on 2005-10-24
I don't remember where I originally got it from. Was way back in the Hoary days.
TRy to see wherein the error lies. Set the Logging directive in /etc/nxserver/node.conf to 7 and look at the output in the log. When there's not enough info look into the session files in the /home/user/.nx dir after setting SESSION_LOG_CLEAN=0 in node.conf.
But, make sure that the client is configure properly first, I'd say.

---

### Post by jtardis on 2005-10-24
Got it!!

Found the error in the session files in the /home/user/.nx dir after setting SESSION_LOG_CLEAN=0 in node.conf as you suggested.

The path to nxdesktop was wrong in the /usr/lib/nx/nxnode file. 

It was giving me /usr/lib/nx/nxdesktop as the path instead of /usr/bin/nxdesktop - a quick edit later and I'm a VERY happy man :D 

Thanks **so** much bugmenot for the assistance, this was starting to drive me a little crazy, now my RDP sessions fly with the power of NX! :cool:

---

### Post by bugmenot on 2005-10-25
let's put that onto the wiki next to the xauth issue...

---

### Post by LanceBrown on 2006-06-16
What exactly did you do to the /usr/lib/nx/nxnode file?

---

