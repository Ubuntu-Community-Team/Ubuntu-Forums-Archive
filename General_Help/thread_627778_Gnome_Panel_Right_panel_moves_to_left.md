---
title: "Gnome Panel: Right panel moves to left"
date: 2007-11-30
forum: General Help
---

### Post by kasio on 2007-11-30
Hi,

I have two panels with launchers, one on the left and one on the right. Whenever start a new session, the right panel is on the left, so there are two. When I try to move it to the right in 'Properties' it immediately goes to 'Left'. I have to expand it, move it to the right, then disable expand. Both panels are not extended and are on autohide.

This is quite annoying. Couldn't find any bugs for it. Any help?

Thanks.

---

### Post by kasio on 2007-11-30
Any1 had the same problem?

---

### Post by kasio on 2007-11-30
Can anyone help me? Or is it just me? Maybe a GNOME problem?

---

### Post by kasio on 2007-12-01
*bump*

REALLY need this fixed

---

### Post by kasio on 2007-12-01
Ah! Doesn't anyone know anything?

I'm going back to Windows.

---

### Post by Pettman on 2008-05-09
I've got a similar problem, two pannels at the bottom of the screen switching place some of the time. Have a look at launchpad's buglists.

---

### Post by machineghost on 2008-05-18
I'm having the same issue.  Two (not very good) workarounds I've found are:

A) Have WINE emulate a virtual desktop ... PROBLEM: you can't get the full resolution this way (because of the app's title bar and any GNOME panels you may have), so you either have to run War3 at a lower resolution or say goodbye to the bottom of your screen.

B) Login to a different account to play War3 ... PROBLEM: you have yo login to a different account every time you want to play War3.

A better solution would be GREATLY appreciated.

---

### Post by machineghost on 2008-05-23
Is there any further information I could provide that would help in diagnosing this issue?

---

### Post by machineghost on 2008-05-25
I figured out a workaround.  First, run winecfg ("Configure Wine" in the Applications menu) and make sure you have Emulate Virtual Desktop on, with the resolution set to your resolution (if you have two monitors and are running TwinView like me, set the resolution to the resolution of ONE monitor).  I have the two boxes above checked too, but I don't know if they are necessary.

Now here comes the tricky part (actually it's really easy; the tricky part was FINDING this part). Go to System => Preferences => Advanced Desktop Effects Settings (if you don't have this, you need to install the compiz configuration manager package).  Next, go down (near the bottom) to the Windows Rules icon and click it.   Go to fullscreen (which should be empty), and change it to class=Wine (if for some reason this doesn't work, open WINE first, then come back here, hit the plus icon, hit "Grab", click on the WIN window, click Add, and that should do it).  Close up the manager, and the next time you start WINE it should be in perfect fullscreen resolution WITHOUT messing up GNOME.

---

