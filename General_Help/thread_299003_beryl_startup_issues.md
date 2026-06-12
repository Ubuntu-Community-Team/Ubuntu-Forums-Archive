---
title: "beryl startup issues"
date: 2006-11-13
forum: General Help
---

### Post by groggyboy on 2006-11-13
I'm having a couple problems with getting beryl to run.

I followed the instructions on the [bery-project wiki]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft").  When I try to set up beryl-manager to run automatically on startup, it doesn't work - only metacity loads.  i have tried putting both "beryl" and "beryl-manager" in System > Preferences > Sessions, but when I load up gnome, they are gone from there.  I have to run beryl manually by typing "beryl-manager" in a terminal.

Alternatively, when I follow the wiki's instructions to set up a seperate X session, it works but the cursor has reverted to the system default instead of the human theme (except when I open an application like firefox).

I'd be happy if someone could help me solve either one (or both) of these issues.

cheers, groggyboy

---

### Post by strabes on 2006-11-13
PLEASE keep the separate login session. that way if something messes up, you can always revert back to your normal metacity session. Anyway, it's beryl-manager, not beryl. To use custom cursors, gtk themes, and icon themes, also add gnome-settings-daemon to gnome-session-properties startup programs. For the other problem, I believe you should also add beryl-xgl to startup with gnome. Then restart x with ctrl+alt+backspace and see if it worked.

---

### Post by groggyboy on 2006-11-13
thanks for trying to help, strabes.

i tried adding "gnome-settings-daemon" to system>preferences>sessions in the beryl xsession, but it didn't work.  at first, it would log on but the gnome start up window wouldn't go away and the cursor was still system default.  the entry i had added to the sessions for "gnome-settings-daemon" was gone.  now i can't even get that far - the beryl session hangs at a white screen right after logging on.

i suspect part of my problem is that my settings in system>preferences>sessions are not sticking, regardless of whether i'm logging in to my regular or my beryl xsession.  i'll test it by putting in an entry for gedit, and report back.

---

### Post by groggyboy on 2006-11-13
i have tested my theory.  i added gedit to my regular gnome startup session.  upon reboot, it was no longer there (however, my home directory and the sessions window were both open - an annoyance, but nothing serious).

i suspect my beryl woes have nothing to do with beryl at all, but with gnome acting up.

---

### Post by strabes on 2006-11-13
that's strange; I've never heard of that happening before. I have no idea sorry lol. Try on #ubuntu?

---

### Post by groggyboy on 2006-11-13
My sessions manager problem was solved in this thread:
[http://www.ubuntuforums.org/showthread.php?t=286508]("http://www.ubuntuforums.org/showthread.php?t=286508")

However, logging in to the beryl session usually still results in a white screen and the cursor.  Only one out of my last four attempts to log in has worked.

---

### Post by groggyboy on 2006-11-13
...and if i get past the white screen, i usually get something like the screenshot i've posted.

three problems with that picture: the startup screen is still there, the cursor is still system default, and by the beryl diamond there should be both a networkmanager icon and a power-manager icon.

altho, in the time it took me to write this post, the two missing icons have appeared and the startup screen has disappeared.  apparently gnome with beryl has variable load times? (meaning: usually it takes forever to get to the loading screen, after which it often takes even longer to load the apps, but sometimes it all loads up fast and promptly - hmm...)

oh well, i guess beryl IS experimental...

---

### Post by groggyboy on 2006-11-18
if anyone should have the same cursor issue, i found the solution on the beryl wiki.  when creating the xsession startup script for Beryl, instead of using:> #!/bin/sh
beryl-manager
sleep 4
exec gnome-session #(or 'exec startkde' for kubuntu)
use this instead for the last line:> exec /etc/X11/Xsession

apparently, the problem was that xgl (or aiglx) doesn't load mouse configurations.  now to solve the slow loading problem...

---

