---
title: "firefox 3 session restore"
date: 2008-04-25
forum: General Help
---

### Post by rotalever on 2008-04-25
Is there any way to automatically restore the last session using firefox 3 beta 5? It does not work :(

---

### Post by forestpixie on 2008-04-25
Have you tried setting it in preferences - Main Tab - When Firefox starts - usually set to "my home page"

---

### Post by bollix47 on 2008-04-25
Edit > Preferences > General

Under Startup > When Firefox Starts

Select "Show my windows and tabs from last time"

---

### Post by rotalever on 2008-04-25
Yes I did that => nothing happened. I've already tried two different add-ons: Tab mix Plus (no effect), and "session manager". The latter one saves the session and I can load a session through the menu but it does not automatically load the session on startup, even if I tell the addon to do it in the extensions-menu.

---

### Post by bollix47 on 2008-04-25
Try the following:

Remove both of those add-ons.

Restart Firefox.

Select the setting described in post #3.

Open a new tab and go to a site other than the ones already open.

Restart Firefox.

Is the new tab there?

It works on my setup.

If it still doesn't on your setup you might have to check some settings in about:config that relate to cache etc.

---

### Post by rotalever on 2008-04-25
Thank you. It works :D
All tabs were reloaded after startup.

---

### Post by Novus on 2008-04-25
I used session keeper before this upgrade (great extension, but it seams dead so it'll most likely not be available for 3.0)

The built in session restore didn't work for me either. everything in preference was set correctly and nothing wrong with my cache settings, BUT in about:config **browser.sessionstore.enabled** was set to false for some reason (perhaps due to I previusley used session keeper) just changed that to **true** and restart FF 2(!) times (first restart some OLD tabs showed up)

---

### Post by AldenIsZen on 2008-04-25
> **Novus said:**
> I used session keeper before this upgrade (great extension, but it seams dead so it'll most likely not be available for 3.0)

The built in session restore didn't work for me either. everything in preference was set correctly and nothing wrong with my cache settings, BUT in about:config **browser.sessionstore.enabled** was set to false for some reason (perhaps due to I previusley used session keeper) just changed that to **true** and restart FF 2(!) times (first restart some OLD tabs showed up)

I used Tab Mix Plus, which obviously hasn't be enabled in FF3 yet. I tried what you said and it worked. You will have to restart and THEN on the NEXT restart it will work, provided after the first restart when you close FF you choose to allow it to save your session.

update/ I looked up Tab Mix plus on the extension website and you can go [HERE]("http://tmp.garyr.net/dev-builds/") to get the latest Tab Mix Plus build compatible with FF3.

---

### Post by rotalever on 2008-04-25
I wondered why it works now. The key is that I told firefox to clear the browsing history on shutdown. Browsing history must be enabled for session restore.

---

