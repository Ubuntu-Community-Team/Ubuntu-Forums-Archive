---
title: "I saved my session and broke Feisty"
date: 2007-04-25
forum: General Help
---

### Post by baum3046 on 2007-04-25
Hi -

I don't know what happened, but it appears that I broke my installation of Feisty by messing around with saving my session.  I went to System, Preferences, Sessions and chose "Save the Current Session" in hopes that it would make OpenGL load automatically on bootup.

When I logged into Feisty the next time, a lot of things went wrong.  For example, the little computer icon in the system tray (network icon) didn't load.  Also, normally when I logged in I was prompted for my keyring password so I could connect to my wireless network.  That didn't happen either.  I tried to manually connect to my wireless network, but that didn't work either.  Furthermore, when I click on the little red "logout" icon nothing happens.  The only way I can seem to log out is by using "CTRL, ALT, BACKSPACE."

I also have a bunch of applications loading automatically, which I didn't intend.  For example, open office writer opens up.  (this was apparently open when I chose "save the current session."

Does anyone know how to undo the damage I did?  Is there any way to revert to previous session settings?

Thanks for any and all feedback.

---

### Post by elucidblue on 2007-06-12
*bump*

I just ran into the same problem.  Boot time is significantly longer now, and Beryl became so buggy I pretty much have to turn it off.  Is there any way to revert to a previous session?

---

### Post by elucidblue on 2007-06-12
I found a partial solution:  I backed up ~/.nautilus/session and deleted it.  I'm not sure how reliable that is yet, as Beryl was still buggy, but it loads my desktop very quickly and even made it so I don't have to enter my keyring password to access a wireless network.

---

