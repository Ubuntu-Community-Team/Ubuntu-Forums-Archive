---
title: "Ubuntu 6.06 for AMD64 suddenly hangs at boot"
date: 2006-11-17
forum: General Help
---

### Post by devilbush on 2006-11-17
A couple weeks ago I install 6.06 onto my amd64 system and had no problems whatsoever.  I proceeded to install a bunch of typical server apps (apache, samba, subversion) and configured everything to authenticate over LDAP.  I had just installed gnome when I had to shut the machine down to move it a few feet to a different spot.  The box has not successfully booted since. :(

Disabling the splash at boot, the last lines I see on the screen are:

Begin: Running /scripts/init-bottom ...
Done.
 * INIT: version 2.86 booting

At this point, the machine hangs.  Ctrl-Alt-Delete has no effect, but magic keys work and I am able to reboot the machine this way.

I do use a raid 5 array for file storage, but the root filesystem runs off its own drive (along with /var, /home, /usr).  I don't suspect that being the problem, as the arrays seem to reassemble just fine (judging by the on-screen messages), but you never know.  I may as well also mention that the root filesystem is xfs (never tried that fs type before and thought I'd give it a whirl).

I am more or less competent in Linux (tho Google is my crutch), but this is quickly getting beyond my ability to troubleshoot.  If anyone out there has a suggestion on where I could look next, I would be most appreciative. :)

Also, if there is more information that I could provide, please let me know and I'll get right on it.  I can't boot the system directly, but I can boot to cd and poke around the drive as much as necessary.

Thanks!

Michael

---

