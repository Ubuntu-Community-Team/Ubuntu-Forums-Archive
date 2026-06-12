---
title: "Troubles login into session"
date: 2008-05-09
forum: General Help
---

### Post by tomer_le on 2008-05-09
Hey, 
I've installed today AfterImage to try it on my system.
After I've logged off, I can't login normally anymore, I'm getting this error:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.

.xsession-error log shows:
/etc/gsm/Xsession/..
..29 Can't open /main/prompt/sh/init

I've tried looking for this line in Xsession file, but did not find something related to it.

Tried to remove AfterImage and see it it's working - nothing helpful.

---

### Post by ibuclaw on 2008-05-09
Can you try and get the full description of the error your getting please (if there is more).
Then we could debug your problem more efficiently.

But on what you've said, have you tried logging in with the Xclient script?

It should be an option from within your gdm startup page.
Click "Options" in the bottom left-hand corner and choose "Select Session" 

Regards
Iain

---

### Post by tomer_le on 2008-05-09
> **tinivole said:**
> Can you try and get the full description of the error your getting please (if there is more).
Then we could debug your problem more efficiently.

But on what you've said, have you tried logging in with the Xclient script?

It should be an option from within your gdm startup page among the list that you chose the failsafe startup. 

Regards
Iain

This is the C/P of the .xsession-error:
[B]/etc/gdm/Xsession: Beginning session setup...
.: 29: Can't open /main/prompt/sh/init[/B]

I can't log with Xclient, I'm getting the same error.
I'm logged in with failsafe-gnome.

---

### Post by ibuclaw on 2008-05-09
Sorry for the delayed reply...

Hmm. It all seems very curious.

Have you reset your user profile settings?

```
cp /etc/skel/.profile ~/.profile
```
That will reset your login settings to when you first installed Ubuntu.
If there is something erroneous with your user account (and not the system settings), that should fix the error.

Regards
Iain

---

### Post by tomer_le on 2008-05-09
Well I've did it..
the results was quite odd...I did actually managed to log into the session, but everything was black!
No wallpapers, no panels, no windows...nothing except for Cairo-Dock and Compiz expo.
So I've returned to failsafe-gnome..

---

