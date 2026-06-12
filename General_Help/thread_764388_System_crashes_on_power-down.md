---
title: "System crashes on power-down"
date: 2008-04-23
forum: General Help
---

### Post by lodp on 2008-04-23
Hi,

For about a week now I haven't been able to power down my Laptop (running Kubuntu 7.10) in a normal fashion. When I click Log Out> Turn Off, the screen just goes black and the fan starts going crazy. It'll stay like that until I hold down the power button for a "physical" power down.

It's the same when I just log off my user.

I've tried switching off all applications I can get a hold of manually before powering down, but that didn't help.

How can I find out more about this? Are there any logs that survive the reset? This is pretty annoying, and I suppose all those hard resets aren't good for the hardware either..

---

### Post by lodp on 2008-04-29
I upgraded to Hardy and the problem persists. I did notice that if I hit shut-down and press the power button once after 30seconds or so, the system will shut down regularly about 50 percent of the time. 

That's curious because the power button doesn't do anything when pressed during a regular session (i.e. without having clicked Log Out > Turn Off first).

BTW, I'm using proprietary drivers (fglrx) for my ATI mobility Radeon graphics card, if that has any relevance.

---

### Post by jalefkowit on 2008-04-29
I'm seeing the same issue on my PC with Kubuntu Hardy, also with an ATI graphics card (X1950 Pro), with restricted driver installed and Compiz desktop effects activated.

Anyone out there have any ideas on what might be causing it?

---

### Post by lodp on 2008-05-03
I tried de-activating the restricted driver and using the "ati" driver instead. That fixed the issue.

I also found this bug report here, which seems to be referring to the same thing:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605)

somebody posted a fix that i'll try now:



> I had the same problem on my up to date Kubuntu 8.04 Beta. The problem is that /etc/ati/authatieventsd.sh can't locate a file. It's got the wrong path.

**In /etc/ati/authatieventsd.sh change this line:**
   XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*

**to:**
   XDM_AUTH_MASK=/var/run/xauth/A$1*

This solved the black screen hanging on logoff for me.

I'm not quite sure what to change if you're using Gnome, but I suspect it's this line:
    GDM_AUTH_FILE=/var/lib/gdm/$1.Xauth

**EDIT**: The fix worked!

---

### Post by jalefkowit on 2008-05-04
Thanks lodp, that appears to have done the trick for me too!

---

### Post by lodp on 2008-05-05
Glad to hear it. Let's hope they fix the package soon, it's really quite a nasty problem.

---

