---
title: "Password perpetually incorrect"
date: 2016-01-12
forum: General Help
---

### Post by kevin141 on 2016-01-12
I tried using PamUSB on my usb drive and it didn't work, so i typed in my password manually and it said password incorrect.
So i rebooted to recovery, dropped to a root shell, and uninstalled pamusb, removed pamusb.conf from /etc and the login still didn't work.
So i dropped back to the root shell to change my primary user's password. i changed it successfully using ```
passwd Kevin
```. the new password was still incorrect at the login screen.
So i thought i would make a new user to see if that worked. i created a user named tester with password hello. i rebooted, tried to log into tester with hello and THE PASSWORD WAS STILL INCORRECT!!

I need help with this, it's absolutely mind-boggling.

---

### Post by howefield on 2016-01-12
Thread moved to the "*General Help*" forum.

---

### Post by steeldriver on 2016-01-12
How are you deducing that the password is "incorrect" - there are more reasons than that why a user may not be able to log in to the desktop (for example, non-existent or home directory or incorrect permissions)

---

### Post by kevin141 on 2016-01-12
> **steeldriver said:**
> How are you deducing that the password is "incorrect" - there are more reasons than that why a user may not be able to log in to the desktop (for example, non-existent or home directory or incorrect permissions)

[COLOR=#000000][INDENT][COLOR=#222222]
I figured the red text above the password entry box saying "Incorrect Password" means the password is wrong. Although i can assure you i am typing the password i have saved.[/COLOR][/INDENT]


[/COLOR]

---

