---
title: "Blank screen on logout"
date: 2007-04-23
forum: General Help
---

### Post by cyberdemon on 2007-04-23
My System:
Acer Aspire 5100
AMD Turion 64 MK36 @2ghz
ATI Radion Xpress 1100

OS:
Kubuntu Feisty
kde
manually added xgl session

Drivers:
Manually compiled and installed FGLRX ATI drivers. version: 8.36.5

Software (eye candy):
Beryl

my problem is that logging out of either xgl or kde session results in a black screen. 

I have searched for this problem and have found that several other people are having similar problems with the belief that it is the fglrx drivers. I have done enough tinkering to narrow down the problem not to the drivers but the added command in xorg.conf file to disable composite extentions.

Section "Extensions"
Option "Composite" "false"
EndSection

when this section is removed or set to true, login and logout functions normally however logging into xgl results in a quirky display and beryl does not start.

I have also found a bug report (for edgy) detailing a similar error while using a composite manager 

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/59244](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/59244)

I'm not sure if this is the same problem but it looks like a start. how would I go about applying this patch or making xserver shutdown and restart everytime i needed the login window?

---

### Post by dsegarra on 2007-04-23
I have the same problem. I am using Xubuntu and for some reason logout & Switch User do not work. Have searched as well. I am running with an ATI card.

---

### Post by INFERNO2K on 2007-04-23
An exact same thread with the issue is posted jsut a few threads down on this forum

[http://ubuntuforums.org/showthread.php?t=419688](http://ubuntuforums.org/showthread.php?t=419688)

---

### Post by cyberdemon on 2007-04-23
> **INFERNO2K said:**
> An exact same thread with the issue is posted jsut a few threads down on this forum

[http://ubuntuforums.org/showthread.php?t=419688](http://ubuntuforums.org/showthread.php?t=419688)


I read that thread before posting this new one. this seems to be an entirely diffrent problem.

groovomata posted....

> **groovomata said:**
> I installed feisty on my compaq V5000 laptop and I noticed that I can't Log Out. I Shut Down, Hibernate, Restart (I haven't tried Suspend yet), however Log Out does not work. If I try, I end up with a black screen. If I do <Ctrl><Alt>backspace though, I will be Logged Out. 
Has anyone else had this problem?
Thanks,
Erik.


He says that he has these problems after installing feisty and only has problems logging out. 

I believe this to be an entirely diffrent problem and so posted a new thread.

---

### Post by AaronMT on 2007-04-23
The problem is the exact same. There is nothing different in reading each.

---

### Post by cyberdemon on 2007-04-23
My apologies if the problems seem the same. perhaps I neglected to add diffrent discerning information.

when I Ctrl+Alt+backspace I do not get the logout window. just a black screen.
when I restart I get black screen (does not restart)
when I shutdown I get black screen (no shutdown)

Ctrl+Alt+Del works when at the black screen ONLY when restart has been chosen before the resulting black screen.

these problems only occurred after changing Composit extentions value to false and are repairable if I change 

Section "Extensions"
 Option "Composite" "false"
 EndSection

to

Section "Extensions"
 Option "Composite" "true"
 EndSection

however beryl no longer works.


since I want beryl to work, I was wondering if when I chose logout (or any subsequent features) if there were a way to have xserver restart and then issue the command. it may not be a "fix" but would work for me.

---

### Post by cenora on 2007-06-20
Same problem - after installing Beryl with XGL on an ATI graphics card.

Blank screen when log out - no way to recover besides a forced shutdown (power button).:(

---

### Post by daviddesancho on 2007-06-21
I had the same problem and by the moment restarting X server solves the issue both for switch and logout.

System > Administration > Login Window > Restart X server everytime I logout

I hope a fix comes to solve this issue definitely.
Cheers,

d.

---

### Post by guguma on 2007-08-03
The solution on the other post worked for me:

sudo gedit /etc/conf/X11/gdm/gdm.conf 

Then change AutoRestartServer=false to true.

I have the same graphics card and cpu with the thread starter and I have beryl installed so I presume it will work.

---

### Post by LordMau on 2007-08-04
> **guguma said:**
> The solution on the other post worked for me:

sudo gedit /etc/conf/X11/gdm/gdm.conf 

Then change AutoRestartServer=false to true.

I have the same graphics card and cpu with the thread starter and I have beryl installed so I presume it will work.

Please verify the path you posted for me. I have no "/etc/conf..." folder here, al though there is  a "/etc/X11/gdm" containing gdm.conf.

Thanks.

---

### Post by guguma on 2007-08-07
I am sorry that I am posting late but /etc/X11/gdm.conf will be fine. I am not that much of an expert but if there is no gdm.conf elsewhere than that should be it because there should be a gdm.conf file where Gnome Desktop Manager will read through, if the only one you got is in /etc/X11 then that should do it.

---

### Post by nene3 on 2007-08-07
i am having the same problem... The problem has something to do with ati fgrlx drivers because when i disable them in restricted driver manager logout works again... and i dont run beryl, unless it comes with feisty fresh install (ubuntu newbie here :) ) i will try that solution posted above.. thanks

---

