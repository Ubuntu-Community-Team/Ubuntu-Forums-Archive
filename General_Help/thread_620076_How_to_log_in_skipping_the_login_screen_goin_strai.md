---
title: "How to log in skipping the login screen goin straight to desktop?"
date: 2007-11-22
forum: General Help
---

### Post by UKJim on 2007-11-22
I have changed the security option of auto-login and selected my user, I rebooted and it still took me to the log in screen. 
I would like to turn the power on and go straight to the desktop, I have no mouse or keyboard attached to my ubuntu machine, I want to use TightVNC to remote desktop from my XP machine, this works fine when ubuntu is at the dektop, but when its at login screen the VNC client does not work or show anything. So automatic login will fix this problem as I want to shutdown and startup ubuntu machine when necessary.

Thank you.

---

### Post by mikewhatever on 2007-11-22
Look here [http://ubuntuforums.org/showthread.php?t=617415](http://ubuntuforums.org/showthread.php?t=617415)

I think you must have login enabled if using remote connection.

---

### Post by UKJim on 2007-11-22
as I put in my first post, I have already done that and it still takes me to the login screen after reboot.

---

### Post by UKJim on 2007-11-22
bump**

---

### Post by elamericano on 2008-03-13
It would be nice to go straight to the desktop (display:0), because my laptop may be too weak for multiple sessions, and because I can't add a menu to the panel in display:1. If I drag one to the panel, It gets added to the panel in display:0?!

I've seen a few people with this problem, but no solution yet. Either fix would be welcome - or both ;-)

---

### Post by bodhi.zazen on 2008-03-13
Well, to auto log in :

[http://ubuntuforums.org/showpost.php?p=3203881&postcount=47](http://ubuntuforums.org/showpost.php?p=3203881&postcount=47)

If that is not working, can you give a better description of the problem ?

=============

And to connect via vnc, you do not need to auto log in, just start the vnc server on :1 and vnc in to it.

Example : [uwiki]VNCOverSSH[/uwiki]

You do not need to use ssh, but I advise it as well. You can use putty form windows.

---

### Post by elamericano on 2008-03-13
Ah, define the problem. Well, it's like the first guy said:

1) Connecting via VNC :1 works, but I get a login screen. I'd like to go straight to the desktop. Autologin doesn't help.

2) VNC desktop doesn't have a menu. You can't add one to the panel, because it goes to the :0 panel.

One solution would be to VNC to the :0 display, but I can't. VNC is started by xinetd, but I don't see any options to change what desktop is served. It would be nice to continue to go to the :1 screen if I could customize the empty panels.

 I just noticed that VNC is not in the thread title. Sorry if it seemed offtopic.

---

### Post by bodhi.zazen on 2008-03-13
I think you need to look at your vnc configuration. See the link I gave you, when I vnc into the box I vnc into a desktop.

Personally I use Fluxbox ...

You need to look at ~/.vnc/xstartup

[https://help.ubuntu.com/community/VNCOverSSH#head-700044bef2327e7b99b633bbf5925a49b92feb47](https://help.ubuntu.com/community/VNCOverSSH#head-700044bef2327e7b99b633bbf5925a49b92feb47)

---

### Post by elamericano on 2008-03-13
> **bodhi.zazen said:**
> You need to look at ~/.vnc/xstartup
It doesn't exist.

I think adding gnome-panel or gnome-session to a start up sequence would work, but I can't find it. I did mention it was a xinetd service, right?

---

### Post by bodhi.zazen on 2008-03-13
If ~/.vnc/xstartup does not exist, write one :)

---

### Post by elamericano on 2008-03-20
Finally! I have my menu. I needed to log off at the terminal. If I do that my VNC logon is a full desktop. Well, now that I see what's happening, maybe there's something I can do about it.

I think the xinetd service doesn't use an xstartup. I think that hasn't been understood so far. So, I'll disable the service and start vncserver from initd. Unfortunately, I still can't find a configuration to let me logon remotely and locally at the same time. Even sharing the :0 display would be OK, which is utterly simple to do on Mac and Windows.

Maybe someone out there has this working? Is VNC just going to be crippled if I don't log out?

---

### Post by bodhi.zazen on 2008-03-20
> **elamericano said:**
> Finally! I have my menu. I needed to log off at the terminal. If I do that my VNC logon is a full desktop. Well, now that I see what's happening, maybe there's something I can do about it.

I think the xinetd service doesn't use an xstartup. I think that hasn't been understood so far. So, I'll disable the service and start vncserver from initd. Unfortunately, I still can't find a configuration to let me logon remotely and locally at the same time. Even sharing the :0 display would be OK, which is utterly simple to do on Mac and Windows.

Maybe someone out there has this working? Is VNC just going to be crippled if I don't log out?

Depends on which vnc server you use.

vino an x11vncserver = shared desktop ( :0 ) , so with those two you can log in and share the desktop ( login = :0 and vncserver = :0 also).

vnc4server (vncserver) = unique desktops. Login = :0 ; vnc = :1 

[uwiki]VNC[/uwiki] reviews some of that information.

---

