---
title: "[SOLVED] OOo Impress Full Screen Issue"
date: 2008-05-07
forum: General Help
---

### Post by BandD on 2008-05-07
When I try to run Impress in full screen on a clean Hardy install, the full screen window goes BEHIND the panels (the panels remain on top).  Which equals NOT FULL SCREEN.  Any idea on why this is the case?

Other programs (Totem, F-Spot) work fine in full screen mode.

I use this machine to give bi-weekly presentations on, so this is a pretty serious issue for me.

Any tips or hints would be greatly appreciated.

---

### Post by prshah on 2008-05-07
> **BandD said:**
> When I try to run Impress in full screen on a clean Hardy install, the full screen window goes BEHIND the panels (the panels remain on top).  
Any tips or hints would be greatly appreciated.

Sorry no idea about why Impress does not go fullscreen properly, but a quick tip:

You can enable the hidebuttons for the panel and then, just before your presentation, tuck the panel away in a corner. Right click your panel, choose panel properties, then check (tick) "Show Hide Buttons"

---

### Post by BandD on 2008-05-07
Yeah, but it still shows the buttons when you do that and just looks tacky.  And autohide doesn't fully hide the panels either.  Which, again, looks tacky.

---

### Post by BandD on 2008-05-07
I fixed it.  I had uninstalled and reinstalled the OpenOffice.org suite before, and just to be sure I wnet back through Synaptic to see if any packages might be missing that could be related.  And sure enough, openoffice.org-gnome and openoffice.org-gtk weren't installed.  So I installed both of those, and now everything is good to go!

Stupid me :P

---

### Post by SwimDude0614 on 2010-04-29
I'm having this same issue and both of those packages mentioned above *are* installed.

Also to note, I've updated to OpenOffice.org 3.2 (through ppa i believe, or something like that).

Any other ideas?

---

### Post by BandD on 2010-05-09
I'm having this issue with a newly installed 10.04 system...

I'll look into it and see what I can find out.

---

### Post by medicdave on 2010-05-10
I'm seeing this problem too.

Happens with no Compiz, running Intel graphics, both on amd64 and i386 versions.

Hopefully someone can find a solution to this soon!

medicdave

---

### Post by bubblehead74 on 2010-05-10
Strange. Disabling Compiz helps in my case. You can also try to install Lotus Symphony 3 beta, which does not seem to suffer from this problem:

[http://symphony.lotus.com/software/lotus/symphony/SymphonyBetaHome.nsf/home](http://symphony.lotus.com/software/lotus/symphony/SymphonyBetaHome.nsf/home)

---

### Post by flipper9 on 2010-05-11
How is disabling major parts of the GUI experience and manually hiding toolbars "[SOLVED]".  That's not solved, that's a kludge.

---

### Post by BandD on 2010-05-11
@ flipper9

This thread started 2 YEARS AGO on a Hardy Heron system. (read posts 1-4 and note the dates)  

The issue I had then was solved.  The symptoms are the same but the cause seems to be different.  Post #5 should have probably been a new thread rather than continuing this one.



As a side note, disabling Compiz is a work around.  You can follow progress at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807").  This is the pertinent info for the root cause of this bug:

> 

OOo is not setting _NET_WM_STATE_FULLSCREEN so compiz is refusing to allow it to resize to cover the panel, as it is supposed to. Metacity appears to have a hack for this as when entering presentation mode it says "Window manager warning: Treating resize request of legacy application 0x44045cc (OpenOffice) as a fullscreen request".

We have disabled this workaround in compiz as it causes other problems (with totem, for example). I'd rather not turn this back on, it should be easy enough to drag OpenOffice.org out of the 1990s in this regard. Well, easy for someone who has a computer that can compile it in less than 8 hours.


---

### Post by Hagar Delest on 2010-05-13
Works fine with the Sun version but on xubuntu, worth a try perhaps: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by tolgainci on 2010-07-25
Hello Everyone,

I have the same problem, and openoffice.org-gnome and openoffice.org-gtk are installed. The only workaround for me is to disable compiz before starting a slide show. This is actually not so great, because I really would like to flip my desktop to a Windows installation on Virtualbox using Desktop Cube. I typically make presentations about Windows software at work, and I make a quick demo during the presentation by changing to a different desktop. When desktop effects are disabled, this doesn't look too cool, and you can imagine that my objective is to draw audience attention and impress people with my presentation :)

To put it in a few words, Openoffice.org Impress without Compiz is NOT IMPRESSIVE for me. I'm also not too impressed about the Ubuntu Software Center, which apparently still distributes compiz+openoffice.org with this major bug. 

If anybody has a solution that works when Compiz is still enabled, I will be very glad to hear it. 

Best Regards,

Tolga

---

### Post by BandD on 2010-07-25
The original post is from May **2008**.  Compiz and ooo.org worked fine together then.  This is a different problem with the same symptom.  My problem was solved.  Though I do now suffer from this compiz conflict.  There are several bug reports open regarding this bug.  I'm sure there are quite a few posts whose original problem is this compiz conflict.  

The fact remains that THIS specific thread with it's original problem IS SOLVED.

---

### Post by tolgainci on 2010-07-25
Hi BandD,

Thank you for your reply, I removed my last comment after your post stating that the original problem was indeed solved.

Since you seem to be experiencing the same symptom again, do you happen to know a fix or come across another thread to post this new problem? Or do you think it's worth to start a new thread or contact Canonical official support?

Best Regards,

Tolga

---

### Post by tolgainci on 2010-07-25
Here's a new thread with the "new" issue, my posts here can be removed, left as is or merged with the new thread. I leave that decision to the forum admins, who can judge which best serves the community. As a final note: the new issue with the same symptom has not been resolved yet.

[http://ubuntuforums.org/showthread.php?t=1474754](http://ubuntuforums.org/showthread.php?t=1474754)

---

### Post by tolgainci on 2010-07-27
You can find my workaround for Ubuntu 10.04 below, I hope it helps:

[http://ubuntuforums.org/showthread.php?p=9642347#post9642347](http://ubuntuforums.org/showthread.php?p=9642347#post9642347)

---

### Post by SabreWolfy on 2010-08-17
> **tolgainci said:**
> You can find my workaround for Ubuntu 10.04 below, I hope it helps:

[http://ubuntuforums.org/showthread.php?p=9642347#post9642347](http://ubuntuforums.org/showthread.php?p=9642347#post9642347)

Installing KDE/Kubuntu to "solve" this is much more than a simple "workaround".

---

