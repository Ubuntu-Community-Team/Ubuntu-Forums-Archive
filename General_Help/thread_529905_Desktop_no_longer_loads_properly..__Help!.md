---
title: "Desktop no longer loads properly..  Help!"
date: 2007-08-19
forum: General Help
---

### Post by davidonabus on 2007-08-19
Hey guys.

I've been desperately trying to figure out some solutions ot problems I'd been having..  And in doing so, I think I screwed something up badly.

When I load Ubuntu it gets past the loading screen and I see the background of the desktop (not the wallpaper, mind you) and my mouse pointer.

The Ubuntu graphic that usually appears in the middle of the screen that typically shows what is currently being loaded (nautalis, etc.) never displays..  and I stay stuck on just an orange screen with a mouse pointer.

If I hit CTRL-ALT-DELETE I can see the process manager..  but, apart from this, there's little else I can do.

Is there a way to fix this?

Thanks guys.

david

---

### Post by vambo on 2007-08-19
If you're using gnome, can you login in under a failsafe gnome session?

---

### Post by davidonabus on 2007-08-19
I am using Gnome.  But how do I do what you suggested?  (failsafe)

Thanks.

david

---

### Post by vambo on 2007-08-19
You need to get back to the login screen ie logout
You should have a menu titled "sessions"
Under that there should be a "Failsafe Gnome" entry
Select that and login with normal user name and pwd.
See if you can get a basic desktop.

---

### Post by davidonabus on 2007-08-19
I enabled the option to SKIP a login screen upon boot a few days back..

It auto-logs in..

Any other options?

David

---

### Post by PmDematagoda on 2007-08-19
Doesn't ubuntu ask your username and password upon bootup? Anyway i think you may have to bring up the terminal to make the necessary changes to gnome.

---

### Post by vambo on 2007-08-19
> **davidonabus said:**
> I enabled the option to SKIP a login screen upon boot a few days back..

It auto-logs in..

Any other options?

David

New one on me. How did you manage that? **no** login screen??

---

### Post by davidonabus on 2007-08-19
I fixed it, guys.

Thanks.

I went into recovery mode and just reinstalled Gnome completely.

apt-get install gnome

That did it.

Thanks!

david

---

### Post by davidonabus on 2007-08-19
Oh, and I should add.

Yes, I no longer have a login screen.  I can't remember how I did it.  It was either an option I found somewhere, or a new package I downloaded.  Unsure.  Sorry.

d.

---

### Post by merlinus on 2007-08-19
System/Administration/Login Window/Security.  Enable Automatic Login.

-merlin

---

