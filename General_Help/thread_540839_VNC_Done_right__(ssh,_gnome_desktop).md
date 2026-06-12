---
title: "VNC Done right  (ssh, gnome desktop)"
date: 2007-09-02
forum: General Help
---

### Post by cyberfunk on 2007-09-02
I've read a lot of the how-tos here and on Ubuntu guide as well as at help.ubuntu.com, but I only find old versions of posts that no longer apply and/or don't work.  I'm quite frusterated by my inability to setup this seemingly simple remote VNC setup that I desire.  I am generally competent with the command line, but I lack the detailed understanding of how display management and VNC works in order to get this to work right.  I'm hoping someone will be able to clearly explain how to do the following:

I wish to remotely access an Ubunutu install (Feisty Fawn) via VNC over SSH.  I know how to make the necessary ssh tunnel with  ssh -L 5901:hostname:5901 username@hostname .

Futhermore, I wish to have the vnc session act just like the GDM desktop session I get when I regularly login.   I'd be escatatic if it asked me to login, just like when i'm sitting at my machine in real life. Currently, all I know how to do is run the vncserver command and login remotely to get a single xterm on a grey desktop (Do i need to put something in xstartup in ~/.vnc/ ?  I've tried a bunch of things, but nothing seems to have any effect !  help here?)

Could someone please provide the answers for a frusterated user ? :confused: I've been working on this for what seems like hours, with little to no progress.

Thanks very much in advance,
:)
Cyberfunk


P.S.  I'm running the EMT64 version of Feisty Fawn if that matters (some of the threads I read seemed to indicate broken 64 bit packages).

---

### Post by rdoolen on 2007-09-02
Install FreeNX server on the host and NX client on the client. 

I use it all the time... It  Rocks. 

This is one of my favorite features of Linux.

---

### Post by cyberfunk on 2007-09-02
Unfortunately for various reasons I can't use FreeNX, mostly because I have a lot of people who will only use VNC (long complicated story).  However, I do need VNC to work.

---

### Post by cwaldbieser on 2007-09-03
If  you are seeing just an xterm window, you should be able to start up your window manager by issuing the appropriate command (e.g. gnome-session, startkde, etc.).

The following thread seems to be concern itself with remote login via VNC:
[http://ubuntuforums.org/showthread.php?t=541113]("http://ubuntuforums.org/showthread.php?t=541113")

---

### Post by cyberfunk on 2007-09-03
cwaldbieser,

Recently, the setup has magically started working (and I have no idea why)... however, there is one key problem I can't seem to fix... when I start gnome-session, as you suggest, my Keymapping gets all royally screwed up.

For example, the typing the QWERTY sequence produces the following: c.gvn<?> , and asdf produces abfh.

I have been reading the thread at [http://ubuntuforums.org/showthread.php?t=411949&highlight=vnc+qwerty](http://ubuntuforums.org/showthread.php?t=411949&highlight=vnc+qwerty) , but i'm unsure of which of the many "fixes" I should apply.  There appears to be a lot of ugly keymap-reloading hacks, but i'm unsure of how to execute them, and I'm hoping there's a better an more permanent solution ?

Thanks in advance all.

P.S.  I notice the following output in the xterm window in which I run gnome-session:

"Window Manager Warning:  Log Level 32: could not find XKB extension."

---

### Post by cyberfunk on 2007-09-15
So, does anyone know how to fix the strange keyboard problem ?

---

### Post by clewfirst on 2008-01-24
If you are still having this issue check out:

[http://yclian.blogspot.com/2007/12/3-solutions-to-gnomevnc-keyboard.html](http://yclian.blogspot.com/2007/12/3-solutions-to-gnomevnc-keyboard.html)

Solution number 3 worked for me

---

