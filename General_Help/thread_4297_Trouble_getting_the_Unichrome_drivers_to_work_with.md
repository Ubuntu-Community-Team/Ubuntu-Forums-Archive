---
title: "Trouble getting the Unichrome drivers to work with libGL and DRI"
date: 2004-11-13
forum: General Help
---

### Post by pixelmonkey on 2004-11-13
I'm running Ubuntu 4.10 (Warty), and I am running into trouble trying to get the unichrome drivers (unichrome.sf.net) working with DRI and libGL on my KM400 video chipset (the PC is an Averatec 3225 laptop).

The reason I am turning to the Ubuntu forums (rather than dri-users) for help, is that I noticed on the ViaArena website that someone else has the same exact problem I have AND is running Ubuntu.  Since I don't see this problem showing up on Google except for this other user, and since we both run Ubuntu, I am assuming that this is an Ubuntu-related problem... of course, this assumption could be dead-wrong, it may just be coincedence.

Here is a link to the other user who has the same exact problem as me:

[http://forums.viaarena.com/messageview.cfm?catid=28&threadid=61182&enterthread=y](http://forums.viaarena.com/messageview.cfm?catid=28&threadid=61182&enterthread=y)

Basically, the error message I get when trying to run GL applications (glxgears, glxinfo) is:

libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering

I have tried a million permutations of unichrome drivers, VIA proprietary libraries, drm/dri from CVS, etc.  Nothing gets past this error.

What's strange is that I know another user with this laptop (Dan Morrill, who has a HOWTO for the Averatec 3200 online) who is running Fedora Core 2 and has no problems getting Unichrome-DRI to work.

I should mention that I am using XOrg from CVS, but I have tried, in addition, XFree86 4.3, Xorg 6.8, Xorg 6.8.1, and an ealier CVS build of Xorg (my current build is October 20-something).

I should also note that I don't have XvMC installed at all, so I don't think that's the cause of the problem (as the user on ViaArena suggests).

Does anyone have any ideas, or has anyone gotten unichrome drivers to work on Ubuntu and can report success?

-Andrew

---

