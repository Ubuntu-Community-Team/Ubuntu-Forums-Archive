---
title: "What is &quot;$packagename&quot;?"
date: 2013-12-14
forum: General Help
---

### Post by vasa1 on 2013-12-14
I came across [this]("https://lists.ubuntu.com/archives/xubuntu-devel/2013-December/009537.html"):> Could you share your package-versions of xfce4-indicator-plugin, xfce4-panel and libxfce4ui with us (just to be sure)? (either use something like synaptic or "*apt-cache policy **$**packagename*" from the commandline)
What does the **$** do or is it just a typo? *apt-cache policy packagename* is what I've usually seen and used.

---

### Post by Toz on 2013-12-14
Hi vasa1.

Consider this:
```
packagename="blah-blah-blah"
echo $packagename
```

I believe that in that thread that you linked to, the author is using $packagename as a placeholder for:
- xfce4-indicator-plugin
- xfce4-panel
- libxfce4ui

---

### Post by vasa1 on 2013-12-15
Thank you :)

That's what I get for trying to understand dev-speak!

---

