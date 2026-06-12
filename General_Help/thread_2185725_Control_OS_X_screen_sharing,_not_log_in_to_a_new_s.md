---
title: "Control OS X screen sharing, not log in to a new session via VNC"
date: 2013-11-03
forum: General Help
---

### Post by leamanc on 2013-11-03
Hello,

I am currently running Ubuntu 13.10, and have a couple of Macs, one running 10.6.8, the other 10.9.

It used to be in Ubuntu that when I connected via VNC, using Ubuntu's Remote Desktop Connection app, that I could control the screen of the Mac, in the currently logged-in session.

Somewhere along the line, this stopped working the way I would like.  Now Ubuntu's Remote Desktop (Remmina) will connect, but take me to the login screen on the Mac.  From there, I can log in to a new session on the Mac -- similar to Citrix or RDP on Windows.

Is there a way to get Ubuntu to just control the screen of the currently logged-in session?  I at first thought that the change was due to Apple changing things since OS X 10.7, but then I recalled that the OS X 10.6.8 machine has not changed, but Ubuntu's Remote Desktop app's behavior has changed.

Sorry if this has been discussed elsewhere, but I could not find the issue with a search of the forums.

On both the 10.6.8 machine and the 10.9 box, I have Remote Management turned on in OS X's System Preferences.  But I have also the options checked in there so that "Anyone may request to control the screen" and that "VNC viewers may connect with the password: *****".

Do I need to try a different app on Ubuntu?  If so, which one?

Thanks in advance!

---

### Post by leamanc on 2013-11-04
I've found a solution that works for me.

I installed xtightvncviewer.  When trying to connect to the 10.9 machine, I still get the login screen.  But when I connect to the 10.6.8 machine, I can control the screen of the logged-in session.

From the 10.6.8 VNC session, I can use Apple's Screen Sharing to connect to the 10.9 machine.

So, it works great for 10.6.8; it's a little convoluted to get to the 10.9 machine. But this is just for me at home; it's not like I'm needing to find a solution in a lab or enterprise environment. :D

I'd still like some suggestions from the community so that I can connect to 10.9's logged-in screen directly, because I'd like to retire the 10.6.8 box sooner or later.  But what I've found works for me now.

---

