---
title: "Kontact icon won't stay in tray"
date: 2006-12-30
forum: General Help
---

### Post by martal on 2006-12-30
My two icons for Kontact and KOrganiser Reminder will not stay in the sytem tray together. One or other or both move to the top left of the desktop, and sit in front of other programs. This is very annoying since I've just come to use the superb Kontact app and imported all Thunderbird data.

My session is set to save, I make it clean, ie take out all running Korganiser etc processes, nothing related in Startup programs. I logout and back in to make sure I can start clean.

Then I add the one entry: /usr/bin/kontact to Startup Programs in Sessions. When i log back in, sometimes the two icons are sitting nicely in the system tray, sometimes one or both are on the desktop. If they are together, they never stay that way for long.

Any ideas? (Running Unbuntu Edgy with Gnome and many KDE apps).

---

### Post by martal on 2007-01-03
Replying to my own post.

The situation has become clearer and more stable but the main problem remains.

First, the save or not save session in System | Preferences | Sessions has been resolved. There is a bug here which other users have also seen. When save session is set to not save, on the next login the Sessions window is up and also a file manager window. Prevent this by setting your session as you want it (in my case, no running Kontact or associated processes) and not save session checked, then run the command gnome-session-save (Alt-F2). Should be clean session at next login. If not, repeat.

Second, I made things clearer by not having Kontact run as a startup program. I just launch it from a panel icon.

Consistent result now: Kontact icon in the tray, KOrganizer Reminder daemon icon on the top left of the desktop, sitting over where a maximized window control button is. :( 

Since it really definitely should be in the tray, I'm going to make another post, since this original has changed somewhat.

---

