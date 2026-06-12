---
title: "Compiz crashed; lost settings"
date: 2008-06-10
forum: General Help
---

### Post by toadliy on 2008-06-10
Last night I was on Pidgin when for a brief second the title bars on all my open windows disappeared. Upon reappearing, they were replaced by the default Metacity title bars. I assumed that Compiz had crashed, so I checked in Appearance and "Normal" was selected instead of "Custom." (Does that happen automatically when Compiz crashes?)

I selected Custom again and compiz came back up, but all the settings were returned to default. Upon booting up again this morning, my custom animation settings were restored, but the selected plugins were still at default settings, as well as my desktop size.

I'm not concerned about getting my settings back--that took me all of 30 seconds--but does anyone know what exactly happened to cause me to lose my settings?

Thanks in advance.

---

### Post by Forlong on 2008-06-10
Sounds like a problem in gconf.

You can switch to the flatfile backend (which makes use of a plain text file) in ccsm's preferences, to avoid something like this in the future.

---

