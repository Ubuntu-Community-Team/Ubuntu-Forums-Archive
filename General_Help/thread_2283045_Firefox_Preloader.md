---
title: "Firefox Preloader"
date: 2015-06-18
forum: General Help
---

### Post by jasonbyrne-att on 2015-06-18
Is there anything like Firefox Preloader (for windows) that will preload FF specifically in Ubuntu ? I already know about prelink and preload.

---

### Post by papibe on 2015-06-18
> **jasonbyrne-att said:**
> ... prelink and preload.
I believe you pretty much got it.

Are you talking 'preload' like an startup application? That is, that it opens automatically when you login?

Regards.

---

### Post by v3.xx on 2015-06-18
> **jasonbyrne-att said:**
> Is there anything like Firefox Preloader (for windows)

Firefox Preloader for Linux?

[https://addons.mozilla.org/en-us/firefox/addon/firefox-preloader/](https://addons.mozilla.org/en-us/firefox/addon/firefox-preloader/)

---

### Post by kerry_s on 2015-06-18
i been looking in to a program called profile-sync-daemon, you install it via ppa.
[http://linuxg.net/profile-sync-daemon/](http://linuxg.net/profile-sync-daemon/)

i haven't tried it yet myself, as i'm on ubuntu-mate 15.04, not 14.04, so not sure it is built for my version yet.

---

### Post by kostkon on 2015-06-18
> **v3.xx said:**
> Firefox Preloader for Linux?

[https://addons.mozilla.org/en-us/firefox/addon/firefox-preloader/](https://addons.mozilla.org/en-us/firefox/addon/firefox-preloader/)
And the command for adding Firefox (with preload) to your Startup Applications would be:
```
firefox -preloader
```

You can access your Startup Applications from your settings. Open it and then click on Add.

---

### Post by jasonbyrne-att on 2015-06-18
> **papibe said:**
> I believe you pretty much got it.

Are you talking 'preload' like an startup application? That is, that it opens automatically when you login?

Regards.

No not on login, more like preload

---

### Post by jasonbyrne-att on 2015-06-18
> **v3.xx said:**
> Firefox Preloader for Linux?

[https://addons.mozilla.org/en-us/firefox/addon/firefox-preloader/](https://addons.mozilla.org/en-us/firefox/addon/firefox-preloader/)

This looks like it's for windows only, but it installed. I'll see what I can make of it.

---

### Post by jasonbyrne-att on 2015-06-18
> **kerry_s said:**
> i been looking in to a program called profile-sync-daemon, you install it via ppa.
[http://linuxg.net/profile-sync-daemon/](http://linuxg.net/profile-sync-daemon/)

i haven't tried it yet myself, as i'm on ubuntu-mate 15.04, not 14.04, so not sure it is built for my version yet.

From the same developer of profile-cleaner. Thanks for the link.

---

### Post by jasonbyrne-att on 2015-06-19
> **kostkon said:**
> And the command for adding Firefox (with preload) to your Startup Applications would be:
```
firefox -preloader
```

You can access your Startup Applications from your settings. Open it and then click on Add.

It works. Thanks everyone for your responses. Marking solved.

---

