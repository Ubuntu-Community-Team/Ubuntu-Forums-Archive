---
title: "Cups password?? What? [Solved]"
date: 2007-09-04
forum: General Help
---

### Post by telmo on 2007-09-04
Hi, when i try to add a printer in WEB GUI of CUPS ([http://localhost:631/](http://localhost:631/)) it asks me for a password.
Any way to remove this?

I really need help with this!

Thank you

---

### Post by yabbadabbadont on 2007-09-04
Did you try entering your user's password?

---

### Post by s26c.sayan on 2007-09-04
AFAIK, you need to set up a root password, which is disabled by default in Ubuntu!
This can be done using 
```
sudo passwd
```

Then in CUPS web interface:
Username: root
Pass : one whch u have set up

---

### Post by telmo on 2007-09-04
SOLVED! :)
Thank you for your suggestions.

After looking hours for this, i found this solution

```
sudo adduser cupsys shadow
```

Only worked after reboot.

:)

Thanks

---

