---
title: "kmail and kde4"
date: 2008-05-01
forum: General Help
---

### Post by one_ro on 2008-05-01
Hi folks,

Does anyone knows how to start KMail under Kubuntu 8.04 Hardy Heron with KDE4?

Thanks in advance,
Adrian

---

### Post by one_ro on 2008-05-01
BTW, does anyone knows how to revert from KDE4 to KDE3, in case that KMail does not run on KDE4?

Thanks,
Adrian

---

### Post by Butthead on 2008-05-01
Hmm, type "/usr/bin/kmail" into the "run command" box in K Menu? 

Then, (of course!), set it up to show up under the "Internet" sub-menu in K Menu by right clicking on it and farting around with the "Edit Item" menu setting choices until it works and stays where you want it to?

Is that what you mean? :confused:

And yes, it appears to work (so far?) in KDE4.:guitar:

---

### Post by one_ro on 2008-05-02
Ah, yes. Thanks, I tried first by simply typing "kmail" as usual in KDE3, but first time it took about 10 seconds until it started.
After about 5 seconds I thought it's not working, so I postet this message. Then I read over the Internet that it actually does work, so next time I was more patient and finally it appeared.

Cheers,
Adrian

---

### Post by Zorael on 2008-05-02
To permanently migrate from kde4 to kde3, you want to install the **kubuntu-desktop** and remove the **kubuntu-kde4-desktop** packages, either in Synaptic or via a terminal.
```
$ sudo aptitude purge kubuntu-kde4-desktop
$ sudo aptitude install kubuntu-desktop
```
I don't think it'll warn about essential stuff being removed, but if so you likely want to install it the other way around (kubuntu-desktop first, then kubuntu-kde4-desktop).

---

### Post by one_ro on 2008-05-02
Cheers, it's good to know ;)
Adrian

---

