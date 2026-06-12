---
title: "can't find KMail on Ubuntu [Resolved]"
date: 2007-06-04
forum: General Help
---

### Post by yohanes_chin on 2007-06-04
I'm using Ubuntu Feisty and just download KMail, never used it before but wanna try it. But I couldn't find it after the installation is finish. I checked on Applications - Add/Remove and it seems already installed. Here's a screenshot: [http://img2.freeimagehosting.net/image.php?5f01042cae.png](http://img2.freeimagehosting.net/image.php?5f01042cae.png)

Or do we have to using Kubuntu for KMail?

Thanks.

---

### Post by 5-HT on 2007-06-04
The executable will most likely be called kmail (haven't used the program) and can be launched from a terminal or from an Alt+F2. If you want to add an entry into the applications menu for it, you can do so with Alacarte (Main Menu in Sys -> Prefs).

To find the full path to the executable you can do the following in a terminal ```
which kmail
```> **yohanes_chin said:**
> 

Or do we have to using Kubuntu for KMail? 

Nope, you'll just need some KDE libraries that APT will bring in for you.

---

### Post by aysiu on 2007-06-04
Press Alt-F2 and type ```
kmail
```

---

### Post by Feba on 2007-06-04
It's odd that it isn't under Apps->Internet though. Try reinstalling it.

---

### Post by yohanes_chin on 2007-06-04
> **5-HT said:**
> The executable will most likely be called kmail (haven't used the program) and can be launched from a terminal or from an Alt+F2. If you want to add an entry into the applications menu for it, you can do so with Alacarte (Main Menu in Sys -> Prefs).


It works now, find it from (Main Menu in Sys -> Prefs) like you said. Thank you :)

---

