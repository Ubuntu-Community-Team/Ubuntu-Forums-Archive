---
title: "Firefox Adobe flash crash"
date: 2008-05-09
forum: General Help
---

### Post by chcp850 on 2008-05-09
Hi,
I have a well known problem, I think. Firefox (3.0b5 on Ubuntu 8.04) always crashes when I visit any page that uses any flash content. I've tried to install flash player in all different ways. I tried following solution found on web:
1) export XLIB_SKIP_ARGB_VISUALS=1 in /usr/bin/firefox - nothing changed.
2) turning Composite off in /etc/X11/xorg.conf - it is off, no help.
3) witch screen depth from 16 to 24 bits - it was always 24 bits. 

This problem started on Ubuntu 7.10 and FF 2.xx, but after distro upgrade nothing changed. I suspect the new (9.xx) version of flash plugin is to blame, but how to fix this?
For me as a webmaster this problem is a killer, and I can't find any solution so far. Any more ideas?

---

### Post by ibuclaw on 2008-05-09
Have you read the [Ubuntu Complete Streaming Guide]("http://ubuntuforums.org/showthread.php?t=661833")?

It's a very good place to start for all things Adobe on Ubuntu...

Regards
Iain

---

### Post by chcp850 on 2008-05-09
Thanks for an answer, Iain. But it didn't help. I did everything in that page related to flash, but result is the same - FF crashes always when I visit page containing any flash content.

> **tinivole said:**
> Have you read the [Ubuntu Complete Streaming Guide]("http://ubuntuforums.org/showthread.php?t=661833")?

It's a very good place to start for all things Adobe on Ubuntu...

Regards
Iain

---

### Post by ibuclaw on 2008-05-09
Have you tried a Mozilla/Netscape alternative?
Flock, Iceweasel and Swiftfox to name a few.

Also, tryout Opera, to see if it still happens in that.

Another shot in the dark would be to remove your current Firefox user config folder.
Open your home folder and show hidden files. Find "**.mozilla**" and remove it.
All current saved passwords/web content will be removed along with it. And when you re-open Firefox, it will remake the folder and set all setting to how they should be.

Oh, and you are using the package **flashplugin-nonfree 9.0.124.0ubuntu2** from the repository, are you not?

Regards
Iain

---

### Post by chcp850 on 2008-05-09
Thank you for reply, Iain.
I've tried Opera. The browser does not crash, but flash is not working, i.e. nothing is shown in the place where flash content is supposed to be.
So I guess the problem is with flash plugin and I should look for system wide solution perhaps. I've also tried to reinstall FF (also removing .mozilla folder), no luck.
Yes, I'm using newest flashplugin-nonfree from official repository.

---

### Post by Colonel Kilkenny on 2008-05-09
> **chcp850 said:**
> Thank you for reply, Iain.
I've tried Opera. The browser does not crash, but flash is not working, i.e. nothing is shown in the place where flash content is supposed to be.
So I guess the problem is with flash plugin and I should look for system wide solution perhaps. I've also tried to reinstall FF (also removing .mozilla folder), no luck.
Yes, I'm using newest flashplugin-nonfree from official repository.

With Opera 9.27 only flashplugin 9r48 works.
Later versions of flash (I think r124 is the newest) work with Opera 9.5 (although there are still problems).

But the problem is indeed in plugin. Both Opera and Firefox are having trouble with it.

---

### Post by itaintover on 2008-05-09
try uninstalling all firefox flash plugins and install gnash, works for me

---

### Post by chcp850 on 2008-05-10
Hi, the problem with gnash is that:

"Currently it is in a alpha state"
and
"Gnash supports the majority of Flash opcodes up to SWF version 7, and a wide sampling of ActionScript classes for SWF version 8.5"

Lots of sites requires flash v9, so gnash is not a solution...


> **itaintover said:**
> try uninstalling all firefox flash plugins and 
install gnash, works for me

---

