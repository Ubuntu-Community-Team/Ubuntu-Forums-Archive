---
title: "cannot login using XDMCP after local login"
date: 2008-03-09
forum: General Help
---

### Post by damien_d on 2008-03-09
I am a user of 7.10, and I have a problem when logging in via xdmcp.  

The direct symptom is that when I try to login via xdmcp, it appears to start logging in, then I get the background colour and nothing else.  When I shutdown xming, it says there is one client connected.

This only happens to two of the users on my system: damien, which is the default login, and mythtv, which is what I intend on using to automatically log in locally when I finally get mythtv up and happening. Very occasionally, usually straight after a reboot, but not after a local login, I can XDMCP into it using these logins.

However, I have another account (jamie) that I can usually, but not always log into.  I have seen it where I can login using jamie, logout using the gui, then try to login as damien, but get the blank background.  Neither of these users are logged in elsewhere.

I have attached the background of what it looks like.

The same thing happens if I use XWin32 instead of Xming (got a trial to test).  I can forward X over ssh via putty to xming (e.g. $ xclock) without any problems.  It happens with and without my local windows firewall (zonealarm) enabled.

I have seen this problem in Fedora 7 as well (yum update gdm fixed it, then it broke itself again :(  ), and one of several reasons I made the switch to ubuntu.  It made no difference there if iptables was on or off

Does anyone have any ideas?  I'm seriously out of them!

---

### Post by damien_d on 2008-03-09
From a putty session, I can actually start it via:

$ gnome-session

But I would rather use XDMCP over a trusted network - it seems faster when it does work, and it fits in a sub-window rather than taking up my entire desktop.

---

### Post by jdevora on 2008-03-15
I'm having the same problem.

Any ideas?  Any logs that we should look at?

My local X sessions work fine but trying to connect from another system using xming brings me the login screen and after login I only get a screen with the background color.

A ps fax shows:
?        S      0:00  \_ /usr/sbin/gdm
tty9     Ss+    0:02  |   \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt9
?        Ss     0:05  |   \_ /usr/lib/gdm/gdmgreeter
?        S      0:00  \_ /usr/sbin/gdm


Cheers
 JD

---

