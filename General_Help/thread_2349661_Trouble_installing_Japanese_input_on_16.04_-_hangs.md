---
title: "Trouble installing Japanese input on 16.04 - hangs up on Language Support"
date: 2017-01-17
forum: General Help
---

### Post by todd_n on 2017-01-17
Hi all.

I've installed Japanese input on Ubuntu 12. 04.
But, since then I haven't been able to install Japanese input on Ubuntu 16.04.

I have researched it somewhat.
But, the problem now is, when I go to Language Support and I click Install / Remove Languages,
English and Japanese are checked on.  Yet, anthy and mozc still don't show up when I search
in additional input sources in Text Entry.

So, I thought I'd try removing Japanese in Language Support and re-install.  But, when
I un-check Japanese and press apply, then it gets frozen on that with the spinning busy cursor.

Any help is greatly appreciated, as Japanese input is needed for work.

I'd be open to trying through the command-line if anyone can instruct how to.

Thank you.

---

### Post by todd_n on 2017-02-14
Any ideas ?

---

### Post by Perfect Storm on 2017-02-14
Try with:
```
sudo apt-get install language-pack-ja language-pack-gnome-ja language-pack-ja-base language-pack-gnome-ja-base
```

---

