---
title: "Lenovo Ideapad - Touchpad not working"
date: 2021-12-02
forum: General Help
---

### Post by 2CV67 on 2021-12-02
Hi!
I just bought a new Lenovo Ideapad 5-15ARE05-308 specifically to use with Ubuntu.
It works fine with the original Windows 10 & with the upgrade to Windows 11.

I downloaded (& checked OK) Ubuntu 20.04.3LTS & put it on a USB stick with Startup disc creator and booted OK using F12.

I get to the Ubuntu screen asking whether to Try or to Install, but the touchpad is not working so I can't get any further.

Keyboard is OK so I can escape with REISUO...

All suggestions welcome!

Thanks!

---

### Post by tea for one on 2021-12-02
Generally, new hardware may need a more recent kernel.
Try Ubuntu 21.10 in a live session.

---

### Post by jeremy31 on 2021-12-02
Looks like an edit to the grub command line on the ISO is needed [https://askubuntu.com/questions/1248176/ideapad-5-15are05-elan-touchpad-not-working-on-20-04-nor-on-18-04](https://askubuntu.com/questions/1248176/ideapad-5-15are05-elan-touchpad-not-working-on-20-04-nor-on-18-04)
```
GRUB_CMDLINE_LINUX="initcall_blacklist=elants_i2c_driver_init"
```

---

### Post by 2CV67 on 2021-12-02
Thank you both for your rapid & helpful replies!

I started with the simpler option of trying 21.10 & that worked immediately.
So I didn't spend any time on editing command lines...

Consider this one SOLVED.

Thanks again!

---

