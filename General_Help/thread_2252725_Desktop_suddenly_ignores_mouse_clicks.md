---
title: "Desktop suddenly ignores mouse clicks"
date: 2014-11-13
forum: General Help
---

### Post by JKyleOKC on 2014-11-13
For no apparent reason, my 14.04.1 Desktop began ignoring all mouse clicks this afternoon, They still work on the system menu and all items on both panels, but nothing at all happens on the desktop itself.

I've tried logging out and back in, which did nothing to help, then restarted the system, and finally shut it down for several hours on the outside chance that it might have been heat-related somehow, but nothing has brought it back to normal action.

All icons also disappeared from the desktop after the reboot, and when I powered up after the shutdown the wallpaper had also vanished. I did a quick logout, then switched from the Xubuntu session to the Xfce session before logging back in. That brought the wallpaper back, but not the icons, and all clicks are still ignored.

The desktop files are still in ~/Desktop, and I can launch them from there by selecting the "places" launcher from the top panel, then clicking on "Desktop" to bring it up in Thunar, and finally clicking on the file (I'm configured to launch with a single click, not double click).

I'm fairly certain that some configuration entry has become invalid, but despite long experience with XFCE have absolutely no idea where to begin looking, or which dot-file to delete/rename to force re-initialization...

---

### Post by bashiergui on 2014-11-13
I tend to suspect hardware before config files. Easy way to eliminate that possibility: Check the disk with gparted from a live cd. I guess check with another mouse plugged into another usb port. The erratic behaviour is similar to when the capacitors on my motherboard bulged.

---

### Post by JKyleOKC on 2014-11-14
> **bashiergui said:**
> I tend to suspect hardware before config files. Easy way to eliminate that possibility: Check the disk with gparted from a live cd. I guess check with another mouse plugged into another usb port. The erratic behaviour is similar to when the capacitors on my motherboard bulged.Thanks for the rapid response!

However I fail to see how any hardware failure -- at least at the mouse level -- could make the desktop, and **only** the desktop, ignore clicks. Even more, how it could make the wallpaper vanish! The problem isn't at all erratic; it's quite consistent, just contradictory!

I'll check for possible disk problems, but the several restarts should have already done that automagically.

I've been through the system settings manager, and flushed the session cache, to no avail.

And when re-checking configurations just now, I happened to notice that the number of workspaces -- which I always set to 2 -- had gone back to the default number of 4! That tends to confirm my suspicion that some recent update has modified my system configurations without my knowledge, which if correct would be extremely bad news. I did find one SML file dealing with desktop icons that had unusual entries but cannot locate it again...

---

### Post by ajgreeny on 2014-11-14
Try renaming the **~/.config/xfce4** folder from command line with no xfce4 or xubuntu session running and then login again.

If that works then you will know it is some configuration file/folder in there that is at fault.

---

### Post by Toz on 2014-11-14
> **JKyleOKC said:**
> For no apparent reason, my 14.04.1 Desktop began ignoring all mouse clicks this afternoon, They still work on the system menu and all items on both panels, but nothing at all happens on the desktop itself.
> All icons also disappeared from the desktop after the reboot, and when I powered up after the shutdown the wallpaper had also vanished
Make sure **xfdesktop** is running. If its not, then start it up and see if that helps.

If it does, might be a good time to clear out your sessions cache (Settings Manager >> Session and Startup >> Session >> "Clear saved sessions").

---

### Post by JKyleOKC on 2014-11-14
> **Toz said:**
> Make sure **xfdesktop** is running. If its not, then start it up and see if that helps.

If it does, might be a good time to clear out your sessions cache (Settings Manager >> Session and Startup >> Session >> "Clear saved sessions").Thanks, Toz; that was it! I had already cleared the saved sessions at least twice but that wasn't enough, apparently.

Next question: how do I make sure this doesn't happen again next time I restart this box? I trust I need to double-check the "session and startup" settings to make sure that xfdesktop is checked, but is there anything else I need to do?

---

### Post by Toz on 2014-11-14
> **JKyleOKC said:**
> Thanks, Toz; that was it! I had already cleared the saved sessions at least twice but that wasn't enough, apparently.

Next question: how do I make sure this doesn't happen again next time I restart this box? I trust I need to double-check the "session and startup" settings to make sure that xfdesktop is checked, but is there anything else I need to do?

xfdesktop should be started normally during the xfce load process (started by startxfce4). Sometimes, however, it doesn't. I believe this is because of issues with the saved sessions cache. Unfortunately, it's a difficult bug to pinpoint. It seems that clearing the sessions cache is the best way to accomplish this. 

It would also appear that the best way to clear the sessions cache is to delete the ~/.cache/sessions folder _while not logged in_. It seems that if you clear it while logged in, then log out, the inconsistencies in your system will once again get saved to sessions cache. This may be what happened to you.

---

### Post by ajgreeny on 2014-11-14
In my Session & Startup of the xfce settings manager I have added the following command to the list of startup applications.```
bash -c "rm .cache/sessions/xf*"
```This simply removes any saved sessions from the ~/.cache/sessions folder every time the session starts and removes the possibility of unwanted programmes starting with a new session.

It may be overkill, but it works for me, as I never use saved sessions, so why bother to keep them.

---

### Post by JKyleOKC on 2014-11-14
Thanks for the tip! If the problem returns I'll try it. I usually run my boxes 24/7 to reduce start-up stress on them, so saving sessions makes little sense here either.

---

