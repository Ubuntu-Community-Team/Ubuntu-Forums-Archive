---
title: "Chrome invalid site &quot;Cosmic&quot;"
date: 2018-10-25
forum: General Help
---

### Post by VMC on 2018-10-25
This is strange. Same Chrome version on three Ubuntu's. Xubuntu Cosmic has one site that says is untrusted.
I looked at ca-certificates on all three distros. They match.
The site is:
[ATTACH=CONFIG]281447[/ATTACH]

I have never seen this before. Xubuntu Bionic, Lubuntu Cosmic both have same Chrome ver and the TWC site passes.

---

### Post by deadflowr on 2018-10-25
Looks like it relates to chrome pulling symantec certs support for chrome 70 and on:
[https://support.google.com/chrome/a/answer/7662561?hl=en]("https://support.google.com/chrome/a/answer/7662561?hl=en")

Related chromeblog: [https://security.googleblog.com/2017/09/chromes-plan-to-distrust-symantec.html]("https://security.googleblog.com/2017/09/chromes-plan-to-distrust-symantec.html")

---

### Post by VMC on 2018-10-25
Thanks. Somewhere I did read about symantec, but why on only one distro and not all three.
They all have the exact same install: [COLOR=#5F6368][FONT=Roboto]Version 70.0.3538.77 (Official Build) (64-bit)[/FONT][/COLOR]

---

### Post by VMC on 2018-10-25
I just purged chrome, and re-installed it. It now works.
Something weird though. Previous install had that " face icon" upper right grayed out, even though I was synced up. Now it has the face lit up.

---

