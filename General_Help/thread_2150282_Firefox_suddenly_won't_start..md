---
title: "Firefox suddenly won't start."
date: 2013-05-31
forum: General Help
---

### Post by Cinaed666 on 2013-05-31
After installing an addon, firefox fails to start.
The error in terminal is: GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
I've tried to deleted local data folder and reinstalling it, but the problem persists?

---

### Post by dentaku65 on 2013-05-31
Try to run FF ib safe mode:
```
firefox --safe-mode
```

---

### Post by Doctor Colossus on 2013-06-05
That error message is from [a reported bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=833117") with no fix as of yet, and is probably unrelated. It seems like your problem was caused instead by the add-on, which you could uninstall from safe mode as suggested by dentaku65 or manually, by deleting the extension from your firefox profile directory.

---

