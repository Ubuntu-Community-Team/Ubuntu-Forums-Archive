---
title: "GDM Login Missing Faces"
date: 2008-05-10
forum: General Help
---

### Post by wyth on 2008-05-10
Okay, strange one here.  My GDM login is set to show faces, and there are pictures set for the faces, but no faces are showing up.

Seems like something needs a dpkg-reconfigure or something, but I'm not sure what.

Ideas?

---

### Post by AndyCooll on 2008-05-10
The pictures are usually taken from the System > Preferences > About Me section. Are the faces displaying in that?

:cool:

---

### Post by biasquez on 2008-05-10
same problem, no faces showed in gdm login

---

### Post by ShodanjoDM on 2008-05-10
> **wyth said:**
> Okay, strange one here.  My GDM login is set to show faces, and there are pictures set for the faces, but no faces are showing up.

Seems like something needs a dpkg-reconfigure or something, but I'm not sure what.

Ideas?

Try this:

Get any picture, .jpg or .png (might work also with .gif but I'm not sure), crop/resize to any size (preferably between 96x96px to 128x128px), rename it to ".face" (without quotation marks) and put it in your home folder.

This won't really answers your question, but it works.

---

### Post by Hayjumper on 2008-05-10
I am also having the same problem...  in addition, I've noticed that gdmsetup (started from either the icon under System in gnome-panel, or from the command line via sudo) takes a long time (~2-3 mins) to display.

These issues started occurring today, immediately after installing various updates (bash, wine, evolution, a few others) and rebooting once.  I suspect one of the updated packages is at fault, probably it will be fixed soon as you are clearly not the only person with this problem.

---

### Post by Stemp on 2008-05-10
Same here, no faces.
About me is ok and showing a face, the .face file is ok.
Don't know what's happening.

---

### Post by simontol on 2008-05-10
Same here 'til today updates. I've also noticed that the fast user switch applet displays only the current user.
Does anyone have reported this as a bug?

---

### Post by leoperbo on 2008-05-11
Same problem here, happened after updates suggested in the morning of Saturday 10th, 2008.

---

### Post by jviscosi on 2008-05-11
[This thread]("http://ubuntuforums.org/showthread.php?t=789081") has a link to the [fix]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/228931").

I applied the fix and it brought the faces back for me.

---

### Post by biasquez on 2008-05-11
fixed

---

### Post by wyth on 2008-05-12
Fixed for me and my parents -- cheers all.

---

