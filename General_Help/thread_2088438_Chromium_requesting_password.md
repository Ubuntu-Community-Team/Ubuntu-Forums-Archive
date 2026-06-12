---
title: "Chromium requesting password"
date: 2012-11-26
forum: General Help
---

### Post by lwalper on 2012-11-26
Every time I open Google Chromium I am prompted for my system password. I can cancel the request and everything seems to run fine, but I was just curious if anyone else has this happen?? Why does it want my system password just to use the browser?

---

### Post by pkadeel on 2012-11-26
Most probably you have set Automatic login "ON". This feature bypasses ubuntu gnome keyring which is responsible for storing passwords of applications like your google password used in chromium.

When you open chromium, the gnome keyring asks for your ubuntu password to unlock the password store. Once you unlock it, it will not be asked again during that session even if you close chromium and then reopen it.

---

### Post by lwalper on 2012-11-26
OK, thanks. I disabled the auto Google sign in. That seems to have fixed it. :) We'll see?

---

### Post by crjackson on 2013-02-15
> **lwalper said:**
> OK, thanks. I disabled the auto Google sign in. That seems to have fixed it. :) We'll see?

Where do you find this setting?  I'm having the same problem but I don't see a setting for "Auto Google Sign in"

Thanks.

---

### Post by I2k4 on 2013-05-01
I'd also appreciate details on it - I'm using both Chromium and Firefox on both 12.04 and 13.04 XFCE (on Live USB) and only Chromium has this behavior of bringing up a password dialog.  It can be cancelled with no problem but is a nuisance.

---

