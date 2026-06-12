---
title: "Google Earth - not working now"
date: 2008-05-26
forum: General Help
---

### Post by iheartubuntu on 2008-05-26
Google Earth was working fine the first day or so in 8.04, but last night on my laptop at home I just get a space scene with no earth. Here at work on my desktop Im getting the same thing.

Any tips? Seems like a bug.

---

### Post by iheartubuntu on 2008-05-26
* Bump *

---

### Post by rune0077 on 2008-05-26
It's a weird issue with the installation. Google Earth needs to be run as root (yes, bad design). The only reason it worked for you the first time, was probably because you had used your sudo-password just prior to running it.

So you need to run it like this: alt+F2, then type "gksu google-earth".

---

### Post by Gunman1982 on 2008-05-26
since when must google earth be run as root? ô.O
Can't really tell what the problem is since I use an older version of google earth and that seems to run fine (as normal user).

---

### Post by rune0077 on 2008-05-26
> **Gunman1982 said:**
> since when must google earth be run as root? ô.O
Can't really tell what the problem is since I use an older version of google earth and that seems to run fine (as normal user).

Since the latest beta (I'm assuming that's what the OP has installed). There's a whole thread on it here: [http://ubuntuforums.org/showthread.php?t=758859&highlight=google+earth+awesome](http://ubuntuforums.org/showthread.php?t=758859&highlight=google+earth+awesome)

As you'll see from the thread, this problem comes up for several people. There's a few suggestions on how to fix it (like reinstalling it without using sudo), but nothing that seems a sure fix for everyone.

---

