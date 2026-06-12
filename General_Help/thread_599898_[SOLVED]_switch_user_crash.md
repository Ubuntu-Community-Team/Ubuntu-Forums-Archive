---
title: "[SOLVED] switch user crash"
date: 2007-11-01
forum: General Help
---

### Post by uroskriznar on 2007-11-01
I am using

---

### Post by uroskriznar on 2007-11-01
I am using Ubuntu 7.10 and when I switch users my PC crashes - dark screen. Does anyone have the same problems and is there a solution out there?

---

### Post by cetheriel on 2008-01-01
same thing here.
logging out is ok, switch users crashes. the switch-user applet crashes as well.

---

### Post by FokkerCharlie on 2008-01-03
I have just the same problem.

I have asked on these forums already for a solution / workaround, but none was forthcoming!

Charlie

---

### Post by Doughy on 2008-04-25
Same problem here.  I can't switch users while staying logged into the original.  When I try to come back, everything locks up and screen goes haywire.

---

### Post by alecz20 on 2008-06-25
The only way I can switch users and not get a crash is via the "power button" in the upper left corner and the "Switch User" option.

The fast user switch applet causes the session to reset, or even crash the whole system requiring a "sudo reboot" in tty1

User switch via "Ctrl+Alt+L" (lock screen") closes the initial session.

I'm still looking for a solution.

---

### Post by easy_target on 2008-07-04
Add me to this list. Has anyone already filed a bug report?

---

### Post by alecz20 on 2008-07-07
Just an update to my initial post:

Occasionally, when I try to switch user from the Shutdown menu (having 2 sessions running), I get the prompt to log in in the first session, and second is closed.

To be more clearly:

1) login in session 1
2) switch and login in session 2
3) switch back to session 1
3) try to switch to session 2 and get prompt for session 1. Session 2 crashes at this point (30% chance)

I doubt anyone except those who have this problem are looking at this thread. I think a bug report exists, but there is still no fix.
I find it a bit upsetting that a Linux system famous for stability and multi-user capability crashes so ugly when simply switching users.

Basically, I have to keep my fingers crossed every time I switch the user :(

---

### Post by ryanj1024 on 2008-07-09
alecz20 are you running Rhythmbox?

I have had similar problems on 7.10 and now 8.04 in both cases Rhythmbox was the culprit. 

I have a main account and a gaming account which I like to have logged in at the same time to enable me to have access to a full desktop for messaging / web access in mid game. 

The reason I noticed the source of the problem is that I also like to have music playing on the main account so I can change songs, volume... etc during gameplay. 

Performing the following:

1) Log into main account 
2) Start Rhythmbox 
3) User switch to second account 
4) CTRL ATL F7 back to first account

The first user session will randomly crash (doesn't happen all the time) and respawn on F10. 

If I use Amarok it is stable as a rock.

---

### Post by alecz20 on 2008-07-09
Hey ryanj1024,

I don't use Rhythmbox. Unlike you I don't really like to listen to music when I am playing a game.

The crash frequency is strongly related to the way the user switch is made.

1) via shutdown menu: rarely crashes
2) via fast user-switch applet: almost always
3) via Ctrl+Alt+F6/F7: usually crashes, need more tests
4) via Super+L (lock screen): almost always

I suspect some of the ways are different. It would be nice if they all behaved as case 1 at least.

Also, I am curious how many people have the crash occurring.

Thanks for your suggestion, but even without any programs I have the problem.

---

### Post by ryanj1024 on 2008-07-09
Hmm, 

The other thing that caused me some issues when using multiple X sessions is compiz desktop effects. With desktop effects enabled I found I was getting some very strange crashes. Usually hard locks of the machine, but sometimes causing one X session to crash while gaming.

Not quite what you have described, but it might be worth disabling compiz on both desktops just as a test. 

Not at a Ubuntu machine at the moment but I think its's under appearance preferences -> visual effects/Desktop effects. Change the setting to none.

---

### Post by alecz20 on 2008-07-15
Also see this thread:
[http://ubuntuforums.org/showthread.php?p=5393567](http://ubuntuforums.org/showthread.php?p=5393567)

Now I only get the crash if I use switch user after I lock the screen (Ctrl+Alt+L)

---

