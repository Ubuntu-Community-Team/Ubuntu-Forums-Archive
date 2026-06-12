---
title: "system tay (stalonetray) some help"
date: 2008-05-03
forum: General Help
---

### Post by techno-mole on 2008-05-03
morning, im looking for some help with stalonetray.

im using compiz and awn (this may be causing some of the problems) on hardy (the rc) since finding awn i dont use the panels anymore (found a way to get rid of them altogether, but havent tried it) 
the only problem is that the awn notification area isnt too good (i know its being worked on) so i installed stalonetray, and after some messing around got it to work how i wanted, but i think that compiz isnt actually seeing it as a system tray, but more an open task, which means it wont stick to the desktops, so it will only display on the one it was opened on, and when i rotate the cube it doesnt move it stays on the previous desktop.
doea anybody know how to get round this ? ive tried setting the value in the config file but it still doesnt work.
i read some where that the code might have to be patched to get comiz to see it as a tray rather than a running task, but i would know where to start with that :-)

i have posted before about this, but no one decided to answer (maybe they didnt know the answers to what i was asking) does anyone know of a how to that fixes this issue ? or does anyone know how to fix the issue ?

this is one of the reason i like linux, it does seem to allow for complete customization of almost everything :-)

---

### Post by moonbeam on 2008-05-03
Yes this is a known problem.  I sent a bug report to the stalonetray maintainer approximately a year ago.  I guess the maintainer has decided it was not a bug with stalonetray but with compiz (ect) that doesn't recognize it as a tray. 

```

=== modified file 'src/tray.c'
--- src/tray.c	2007-10-25 14:06:17 +0000
+++ src/tray.c	2007-10-25 14:06:47 +0000
@@ -538,7 +538,7 @@
 		/* TODO: CHECK this with compiz */
 		if (strcmp(settings.wnd_type, _NET_WM_WINDOW_TYPE_NORMAL) == 0)
 			ewmh_add_window_type(tray_data.dpy, tray_data.tray, settings.wnd_type);
-		ewmh_add_window_type(tray_data.dpy, tray_data.tray, _NET_WM_WINDOW_TYPE_NORMAL);
+		ewmh_add_window_type(tray_data.dpy, tray_data.tray, _NET_WM_WINDOW_TYPE_DOCK);
 	}
 
 	return SUCCESS;


```

Above is a patch that should apply against any recent stalonetray sources (I think the oldest I've used it against is approximately 1 year old).  I don't believe there are any patched binary packages for Ubuntu.

It should also be possible to add an entry into the compiz window rules to have it ignore stalonetray though this will not help with other applications that have trouble recognizing it as a systray (awn being one)

---

### Post by techno-mole on 2008-05-03
cheers book marked this page, although i found that the latest version (from the stalonetray website) does work, eg when you set it in the stalonetrayrc config file it doesnt show up as an active task in awn, not sure about compiz though, i think it still scales if you have the scale plugin in enabled (i think thats the one)

i had to re-install hardy thoguh, as i broke it again :) i found a way to get rid of all the panels (was trying to just use awn) but for some reason it messed up the sessions, but i couldnt fix it, even by launching a failsafe session, so maybe ill keep the one panel and ignore it :)

the next thing to do is get this stalonetray to stick to the desktops, eg- when i rotate the cube i want the tray to switch to the next desktop, i know its meant to, but it doesnt.
cheers for the help.

---

