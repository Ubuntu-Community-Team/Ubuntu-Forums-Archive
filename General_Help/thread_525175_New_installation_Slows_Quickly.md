---
title: "New installation Slows Quickly"
date: 2007-08-14
forum: General Help
---

### Post by davidonabus on 2007-08-14
Hey guys!

i'm new to Ubuntu and Linux..  But, so far I'm loving what I'm seeing!

But I have a problem.  And I suspect it may be related to my video card?!  But who knows.

First my system specs:
I just installed Ubuntu 2 days ago.
P4 2.8 Ghz
1.5 Gigs of Ram
X1550 ATI Radeon AGP Card

When I first startup Ubuntu it's speedy!  As it should be.  But after about 25 minutes of usage it really starts to crawl.  I can't even move my Firefox browser around the screen without it skipping, stuttering across the screen instead of moving smoothly (like it does upon first boot).  And when I go to restart the machine normally you'd see a smooth dimming of the screen before the options to shut down, restart, etc. come up..  instead I can literally see the various shades of the dimming drawing in from top to bottom before the shutdown, restart options appear.

So.. I'm thinking that somewhere there's a memory leak!?  Or something.  But it's not Firefox.  Even after I've shut firefox down.. the system still continues to chug.

Currently my system is chugging (time for a reboot).  The system monitor shows about 28% usage on one cpu, and 2% on the other while I sit here idling. 

Any help would be much appreciated.  I really want to stick with Linux!  But I'm concerned that if this is video card related.. that I might have to make the switch back to XP (ugh)

Thanks!

David

EDIT - I just rebooted.  I have the exact same applications open (just firefox, actually) and the system monitor is showing 7% and 4% CPU usage.  All windows move smoothly when dragged.  And if I hit the shutdown button the screen dims smoothly before my shutdown, restart options appear.

---

### Post by davidonabus on 2007-08-14
Does anyone have any idea what might be causing this?  Is my suspicion of the ATI drivers correct?  Or.... ?

Thanks!

---

### Post by YSH on 2007-08-14
Are you using Compiz (3d desktop effects)?

---

### Post by davidonabus on 2007-08-14
No, I'm not using Compiz.. yet.  I think I'd like to, eventually though.

---

### Post by davidonabus on 2007-08-15
Hey guys.. I'm still suffering with this.

If I leave my computer on for any stretch of time.. it will be terribly slow by the time I return.  No obvious reason as to why.

Can anyone suggest some tests that I may be able to run that might help find the culprit?

Thanks!

d.

---

### Post by kellemes on 2007-08-15
Does "top" (in terminal) show any abnormal activity?

---

### Post by davidonabus on 2007-08-17
Hi!

Here is a screenshot of the trmeinal when I run "TOP".  I don't know enough about Linux yet to interpret it correctly.  Can someone take a look at this and let me know if it's showing any strange activity.

This was taken when my computer had slowed down to a crawl.

Top fluctuated between showing what's in the attached screenshot and just showing the user ROOT (not david or haldemo).

Thanks guys!  I appreciate the help.

david

---

### Post by davidonabus on 2007-08-18
Anyone?

Does the above "TOP" screenshot display anything out of the ordinary to explain why my machine becomes so incredibly slow?!

If I knew what the problem was.. I may be able to fix it..

But, as of now, it's starting to look like I may need to go back to XP.. ugh.

d.

---

### Post by forestpixie on 2007-08-18
have yopu actually installed the graphics driver yet?

---

### Post by davidonabus on 2007-08-18
I should add that sometimes command XORG uses up to 70% CPU power (while I'm watching the output from the TOP Comannd)

d.

---

### Post by davidonabus on 2007-08-18
Hey Forrestpixie.

When I run LSPCI from the terminal I get 

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7187
01:00.1 Display controller: ATI Technologies Inc Unknown device 71a7

I believe this is pretty common for the card I have.  ATI Radeon X1550

If I run fglrxinfo I get

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)

So.. I think so.  Does this look right?

Thanks

d.

---

### Post by davidonabus on 2007-08-19
OK.  I see that I may be stuck here. . Not much help coming, which I understand.. as perhaps there is no help that can be given.

But if somebody could just tell me this...

Can a user generally expect LESS performance out of a Ubuntu installation than on an XP installation of the same machine?  Because that is certainly what I've experienced.

I always thought it should have been the other way around.

Thanks.

d.

---

### Post by K.Mandla on 2007-08-19
No, really it should be the other way around. Something is going on with your system that is out of the ordinary.

My first suspicion would be video drivers, since you mentioned that X spikes to 70 percent sometimes. I use a 1Ghz machine with Openbox and an Nvidia card I've never seen X hit 70 percent.

How comfortable are you with experimenting? I mean, is it worth your time and effort to start yanking packages and software from your system, in hopes of finding the culprit? It will be a learning experience, and take some time, but it's a measure of your dedication.

Another idea is to back up all your data, then try a different distribution. If you're still experiencing difficulties with a completely different Linux system, then the issue might be hardware-related.

On the other hand, if other systems run fine, then it's something Ubuntu is doing. In that case, you might be able to troubleshoot the issue. Have you looked for bug reports that resemble your problem?

In any case, don't give up. You'll learn a lot if you have the patience and desire to find out what's going wrong.

---

