---
title: "everything freezes and then all windows moved to same workspace"
date: 2013-10-04
forum: General Help
---

### Post by gleedadswell on 2013-10-04
This is a minor annoyance that has been happening for a while.  Before investigating further and possibly filing a bug report I want to know if it is happening to anybody else.  I googled it and searched on the forum but came up with nobody else reporting it.

I'm running 64 bit Ubuntu 12.04 on an HP laptop with AMD E-350 Processor and Radeon HD 6310 Graphics. 

Every now and then (seems to be most often when I open LibreOffice, but it happens at other times as well) the screen goes momentarily blank, then my desktop graphic reappears with nothing on it.  Finally the launcher reappears and whatever window I was looking at just before this happened.  The whole process usually takes about 5-10 seconds.  After this happens I find that all of my application windows have been moved to workspace 1.  This never seems to happen more than once in a login session.  After it happens everything works works normally again.

I note that I'm running 64 bit Ubuntu 12.04 on another computer (an HP desktop) and never have this problem there, so it seems to be hardware dependent.

---

### Post by enterdavertex on 2013-10-04
Is the graphic card driver's correctly installed ?

---

### Post by gleedadswell on 2013-10-08
Thanks enterdavertex.  Insofar as 3d accelerated graphics work, I seem to have working drivers (i.e. my desktop session is ubuntu, not ubuntu2d).  There are no other graphics problems that I've noticed.  Is there some specific test of my graphics drivers that might be helpful to run?

Bringing up the "Additional Drivers" section of system settings shows one proprietary ATI/AMD driver installed.  It also shows some experimental beta drivers that are not installed.  But those have warnings that they are "intended for testers and early adopters" so I'm loathe to install them.

---

### Post by CatKiller on 2013-10-09
It's Compiz getting itself into a state, crashing and then restarting. The reason your windows end up on the same workspace is because that information isn't preserved by the crash/restart. It's just a common-or-garden Compiz crash.

You can investigate further, but if it's not frequent it might not be worth your time.

---

### Post by a-ciccantelli on 2013-10-09
I think a better description is the unity plugin destabilising compiz.

I was getting so many random crashes and freezes (with versions of ubuntu from 12.04 onwards) on so many different kinds of hardware I have had to switch from unity to using gnome fallback/flashback with compiz.

This is extremely stable on all the hardware I've run it on, some of it five years old and quite low spec.

ubuntu 13.10 with gnome flashback session and compiz configured via ccsm is the best linux desktop I've ever had. Fast, stable and full of features.
Synapse makes a good basic replacement for the unity dash.

Hopefully unity 8 will work better as it isn't a  massive compiz plugin ?

---

### Post by gleedadswell on 2013-10-15
OK, that's more or less what I figured.  This is, at most, a minor annoyance.  I actually really like Unity (which I know will make many readers scoff).  So I think I'll just put up with this one minor quirk.  But if I get the itch to fiddle with my desktop for fun, which I do occasionally, I'll definitely try out the gnome flashback with compiz and synapse that a-ciccantelli speaks so highly of.

Aside from the possibility of Unity 8 fixing this, since it only happens to me when I open LibreOffice, I'm also hopeful that a future version of LibreOffice might fix this.

Cheers!

---

