---
title: "Long GDM Login Periods!"
date: 2005-10-24
forum: General Help
---

### Post by dlovecraft on 2005-10-24
Hello All.

I've just switched over to Ubuntu after hearing so many lovely things about it.  One less for SuSE, one for Ubuntu, at any rate.

So here's the thing.  I am having some very strange login issues with gdm.  I installed with no problem, and have a system up and running.  Got ndiswrapper together in a couple of minutes, again with no problem.  Being the lover of eye-candy I am, I switched the GDM and splash pictures, because that sort of thing keeps me going.  The issue comes when I try to login with that GDM once I had rebooted.

If I try to login as normal, nothing happens at all.  I get the brown background, no splash, no GNOME session.  Nada.

If I login as root (I know, security and all that, but I was testing) then the above happens again.  In fact, it happens with any user I make up.

If I login as failsafe, again, the above.

If I use a failsafe terminal, I can bring up metacity and apps as usual.  The interesting bit bit is if I type gnome-session, I get nothing happen for about two minutes.  Then, the session appears.  After this, subsequent logins are as normal.  Until I have to reboot, that is, when the whole thing starts again.

Nothing interesting shows up in dmesg that I recognise, although there are a lot of messages by atkbd.c telling me that unknown keys have been pressed.  Stuff like:

[4299015.866000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299015.968000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).

In fact, that message over and over again, which I don't recognise.

I'm not a newbie at Linux, although I have been having to use MacOSX and Solaris for a couple of years, so have been in the wilderness.  But this has me stumped. :confused: 

Any help and advice on what to post for further diagnosis would be gratefully received.

Ta in advance. :D 


Dela

---

