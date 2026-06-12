---
title: "VNC Viewer, can't type password"
date: 2007-10-28
forum: General Help
---

### Post by posterberg on 2007-10-28
I have problems with VNCviewer after upgrading to Gutsy.

It seems that the vncviewer in Gutsy supports usernames and passwords and also has a more gnomeified look than the old viewer. I do however have problems with the new login interface, it is impossible to set focus in the password field which of course makes it rather hard to connect to remote desktops.

I have the exact same problem whether I run vncviewer from command line or via the Terminal Server Client.

Clues?

/p

---

### Post by erwall on 2007-10-28
bump, having the same problem!

---

### Post by Jose Catre-Vandis on 2007-10-28
See this, it's a workaround, but it fixed it for me :)

[http://ubuntuforums.org/showthread.php?p=3649566#post3649566](http://ubuntuforums.org/showthread.php?p=3649566#post3649566)

---

### Post by erwall on 2007-10-28
> **Jose Catre-Vandis said:**
> See this, it's a workaround, but it fixed it for me :)

[http://ubuntuforums.org/showthread.php?p=3649566#post3649566](http://ubuntuforums.org/showthread.php?p=3649566#post3649566)
Thanks, that worked great.  Maybe it'll be fixed in an update or something...

---

### Post by posterberg on 2007-10-28
Ok thanks, I'd prefer solving it with the non-working software rather than installing  a new one. But I can see that your solution should solve the problem... ;o)

---

### Post by Jose Catre-Vandis on 2007-10-28
> **posterberg said:**
> Ok thanks, I'd prefer solving it with the non-working software rather than installing  a new one.)

Agreed :)

---

### Post by jf1991999 on 2007-10-28
I had this exact same problem.  I was able to occasionally get focus on the password field and after playing around found that if you click close to the left part of the password field you get focus on the field and are then able to enter the password.  Somtimes you have to wait for a second or two for the cursor to appear and sometimes it never appears and you have to restart.

This is certainly an annoying bug.

---

### Post by timcredible on 2007-10-30
if vnc isn't working for you, try xdm, it's the linux/unix standard, and i know it works on gutsy, because i'm using it right now.  my how-to on xdm:
[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1)

---

### Post by sefs on 2007-10-30
1) left click in the field you cannot set focus too and keep depressed
2) click on the right mouse button with left mouse button still depressed, and release right mouse button and left mouse button
3) cursor will magically appear in pesky field
4) type in password

This should work 100% of the time, and as you get nimble with it ... it would be like performing a single left click as one should

---

### Post by Jose Catre-Vandis on 2007-10-30
> **sefs said:**
> 1) left click in the field you cannot set focus too and keep depressed
2) click on the right mouse button with left mouse button still depressed, and release right mouse button and left mouse button
3) cursor will magically appear in pesky field
4) type in password

This should work 100% of the time, and as you get nimble with it ... it would be like performing a single left click as one should


Well, I went to try this, and as soon as I clicked in the password box I had focus, could type the password and access my remote PC. Worked three times in a row too. Anyone else got automagically fixed?

Thanks for the tip :)

---

### Post by m0shen on 2007-10-31
The right then left mouse button trick works for me.  I also noticed that middle clicking in the field brings it into focus as well.

---

### Post by gibbsuk on 2007-11-29
> **sefs said:**
> 1) left click in the field you cannot set focus too and keep depressed
2) click on the right mouse button with left mouse button still depressed, and release right mouse button and left mouse button
3) cursor will magically appear in pesky field
4) type in password

This should work 100% of the time, and as you get nimble with it ... it would be like performing a single left click as one should

This worked for me - cheers!

---

