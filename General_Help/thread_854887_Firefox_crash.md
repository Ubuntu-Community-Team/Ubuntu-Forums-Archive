---
title: "Firefox crash"
date: 2008-07-09
forum: General Help
---

### Post by jgomo3 on 2008-07-09
Ubuntu 8.04. Firefox 3.
If i close the tab with gmail, firefox crash.

---

### Post by arm-c on 2008-07-09
Might be a plugin issue.

If you have the Prism plugin installed, try disabling it.  That is known to cause sudden crash after a download.

If you have other plugins installed, try disabling them and restarting to see if it fixes problem... then reenable them one by one until you ID the conflicting plugin... but plugins might not be your issue.

I tried here and couldn't recreate your problem.  I am using v.3.0 of firefox.

Try installing a different browser and see if you stil have same problem. Try Epiphany through Add / Remove programs and also try "google gmail" prism application.  Prism should get installed, but note that it is NOT the prism firefox plugin, but a separate application.

---

### Post by jgomo3 on 2008-07-09
I disabled all plugins and add-ons, i run firefox with the -safe-mode option and nothing. But on the console from where i runned "firefox -safe-mode" was revealed the problem: segmentation fault.

I tryed with epiphany but epiphany didn't crash. I noticed that epiphany and firefox do the same thing on the console, they print:

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

many times, but firefox crash with the segmentation fault.

---

### Post by arm-c on 2008-07-10
I have to bump on the segmentation fault.

----

You might see if Prism works for gmail.  I use prism all the time and it uses the firefox engine.  Sorry couldn't be of more help.

---

### Post by jgomo3 on 2008-07-25
Rosolved by the last update of the package firefox-3.0 at the date of july 25 of 2008.

I hate to wait for stuff like this.

---

