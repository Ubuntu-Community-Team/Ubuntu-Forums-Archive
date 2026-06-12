---
title: "Another GNOME black screen (a little different though)"
date: 2008-01-17
forum: General Help
---

### Post by silverpig on 2008-01-17
People seem to be having similar problems to me, but I think mine is a little worse.

Everything worked with my laptop this morning until I rebooted to bring it to work. Several updates had been applied although I do not know which ones.

gdm starts up fine.

When I log in using the default session (Gnome with compiz), I hear the startup sound and the screen goes black. The cursor is an X in the middle of the screen, and responds to movement, but I can't do anything.

I can get back to gdm using <ctrl><alt><bksp>

When I log in using the Gnome or Gnome Failsafe sessions, I get the same thing, except the cursor is a little arrow.

I can log in to failsafe terminal just fine. In the terminal session, I can sudo myself a gnome panel, but I cannot start one up with my normal user.

I used this sudo gnome panel to create a new user. This new user can log in just fine, gnome starts up and everything is happy. I can enable GL Desktop and all the effects and they work well too.

Logging in after this with my first user shows no change. I still can't do anything.

I logged back in with the second user, and moved .gnome .gnome2 .gconf .metacity to <directory name>-old and tried logging in with the first user again. Still no change.

When stuck, I can <ctrl><alt><F2> and do things with that terminal.

I tried installing dbus-X11 to no avail. I can't open gnome-session-manager in my old account to change anything.

What happened to my old account? The new one works great, but I'd like to fix the old one rather than transfer everything over.

---

### Post by kdwillia on 2008-01-17
I had this issue and was able to somehow "repair" GNOME.

I had KDE on the machine as well and ended up logging into a KDE session using the same login name.    Then logged out and logged into a GNOME session.   Somehow, it worked.

---

### Post by silverpig on 2008-01-17
Thanks. I'll try installing xubuntu-desktop or something and will log in with that. I guess the failsafe terminal doesn't count :P

---

### Post by kdwillia on 2008-01-17
No, the failsafe didn't work for me because I tried that too.   I was disappointed because I thought that I was going to have to switch to using KDE and I had become very accustomed  to using GNOME.

Was very happy when I tried to log back into GNOME and it worked.

---

### Post by silverpig on 2008-01-17
Nope that didn't work. On my last <ctrl><alt><bksp> I noticed a brief error message. I checked the logs and found:


Jan 17 10:25:52 titan kernel: [  554.044000] [fglrx:firegl_lock] *ERROR* Process 5544 is using illegal context 0x00000004

---

### Post by kdwillia on 2008-01-17
Well, at least now we know that we are working with something to do with the video driver :)

Can you edit your xorg.conf to use the basic vesa driver and get back into GNOME.   Then reload the ATI drivers.  Also, did you use Envy to install your ATI drivers?   If so, you may need to rerun Envy if updates have taken place.

---

### Post by silverpig on 2008-01-17
No envy was used. This is a fairly fresh install (~1 month old) of 7.10. I just enabled the ati driver through the restricted drivers manager, rebooted, then enabled GL desktop.

I don't really see how it could be the driver as I'm using the same driver and xorg.conf in my new user. There's gotta be some setting set in my other account that is causing this.

---

### Post by silverpig on 2008-01-18
UPDATE:

Okay it just works now?

A few reboots later and everything is back to normal. I don't quite get it, but whatever.

---

### Post by kdwillia on 2008-01-18
Seems like the same thing that mine did.   Didn't work... and then ta da   Back into GNOME.

Maybe the Linux Gods were smiling on you today :)

---

