---
title: "Problem With Monitor!!!!!!!!!!!"
date: 2008-06-16
forum: General Help
---

### Post by DexterLB on 2008-06-16
So, I have ubunto for 1 year by now. Yesterday my friend wanted I to install ubuntu on his PC also. And I did. But today he's changed his monitor. And when ubuntu starts the startup screen shows, everything is good until the time when GDM starts. Then the monitor says "UNSUPPORTED MODE". I hear the "drum" sound for login, so GDM has started. Any ideas??????? :confused::confused:

---

### Post by kpkeerthi on 2008-06-16
Boot with the recovery mode and run this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Type **reboot** and boot normally.

---

### Post by natirips on 2008-06-16
Edit: kpkeerthi was faster than me, you can probably ignore this post.

This probably won't be of much help, but I think the login screen uses 1024x768 resolution. But then again, I think every single modern monitor in the world should support that resolution (except maybe some TVs).

If you know how to work with the console, try CTRL+ALT+F1 at the login screen to login to a full-screen console. CTRL+ALT+F7 to get back to graphical user interface.

Unfortunately I don't know how to change the logon screen resolution from the console, but try searching the forums or googling for it.

---

### Post by DexterLB on 2008-06-17
Yes, it uses 1024X768, but the monitor supports it. I think the problem is with the frequency - the old monitor supported 75Hz and the new one supports 60Hz. I tried reconfiguring xorg but it doesn't help. Is there a way to set the frequency in xorg.conf?

---

### Post by rockstarrem on 2008-06-17
Have you tried playing with the monitor settings itself, like moving the picture from left to right? Also, have you tried logging in and seeing it the monitor switches to the correct resolution? Can you even login?

If you can login I'd try changing the resolution from the GUI and see what happens. You've probably tried all of this but I'm trying to help :P.

---

### Post by DexterLB on 2008-06-17
Nice idea! I can login, but I can't see the gui. So, can I force ubuntu to start in low-graphics mode?

---

