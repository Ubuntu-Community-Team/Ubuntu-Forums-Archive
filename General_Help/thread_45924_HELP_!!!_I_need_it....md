---
title: "HELP !!! I need it..."
date: 2005-07-02
forum: General Help
---

### Post by hasenkamp on 2005-07-02
Please I need help !!!

I need do some work on a computer that I only can reach by other one, what means that I only have remote access.

What I did:
=================================================

local$ xhost +
local$ ssh -l blablabla remote.computer

#once I logged on

remote$ export DISPLAY=local_ip:0.0

#but I couldn't get any return runnig X applications... se the result trying to open xterm.

remote$ xterm
xterm Xt error: can't open display: local_ip:0.0

=================================================
just to test I tryed from other computer running slackware and this process have worked fine.

I also tryed:
local$ ssh -Y -l blablabla remote.computer
local$ ssh -X -l blablabla remote.computer
local$ ssh -Y -X -l blablabla remote.computer

but none of then have worked... ](*,) 

in advance, thanks for the help.

---

### Post by crashtest on 2005-07-02
[QUOTE=hasenkamp]Please I need help !!!

I need do some work on a computer that I only can reach by other one, what means that I only have remote access.

What I did:
=================================================

local$ xhost +
local$ ssh -l blablabla remote.computer

#once I logged on

remote$ export DISPLAY=local_ip:0.0

#but I couldn't get any return runnig X applications... se the result trying to open xterm.

remote$ xterm
xterm Xt error: can't open display: local_ip:0.0

=================================================
just to test I tryed from other computer running slackware and this process have worked fine.

I also tryed:
local$ ssh -Y -l blablabla remote.computer
local$ ssh -X -l blablabla remote.computer
local$ ssh -Y -X -l blablabla remote.computer

but none of then have worked... ](*,) 

in advance, thanks for the help.[/QUOTE]


I also found this very frustrating, and your post prompted me to find a solution.  First of all, allowing remote connections to your xserver is considered a security risk, and Ubuntu ships with this disabled by default.  The conventional wisdom is that you can ssh -X to the remote machine, and porting the display back to your local machine, and all authentication is supposed to be handled for you.  (i.e. no need to do xhost +).  This does not work for me.

The way to do things the 'old way' as many of us are used to is as follows:
-edit /etc/gdm/gdm.conf and in the [security] section, change the line 'DisallowTCP=true' to 'DisallowTCP=false'.  Now restart your Xserver.  Note: you can also do this by running gdmsetup, and on the Security tab, clear the checkbox beside 'Always disallow TCP connections to X server'.  Again,  you must restart the Xserver before this will work.

Keep in mind the security hole that is opened up if you do this.  At a minimum you should avoid doing xhost +, and instead only do xhost <specific IP> so that incoming connections are limited to a specific trusted host.

---

### Post by hasenkamp on 2005-07-02
Ok thanks !!!

I'll try this an then I post here again.

Another thing, and if I'm using KDM insted GDM? how can I proceeed?

Thanks.

---

### Post by crashtest on 2005-07-02
[QUOTE=hasenkamp]Ok thanks !!!

I'll try this an then I post here again.

Another thing, and if I'm using KDM insted GDM? how can I proceeed?

Thanks.[/QUOTE]


I don't know anything about KDM, but I'm sure the same security has been applied - i.e. disable TCP connections to the xserver.  Maybe you should just try ssh -X first? A search on these forums will turn up more information on this.

---

### Post by hasenkamp on 2005-07-03
THANKS !!!

I tried what you said and worked...

As I use kubuntu I just installed the GDM and applied the changes.
As soon as I discover where I can make the changes on KDM I post one reply here.

cya

---

