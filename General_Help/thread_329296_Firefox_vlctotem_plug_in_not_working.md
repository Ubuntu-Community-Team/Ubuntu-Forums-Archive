---
title: "Firefox vlc/totem plug in not working"
date: 2007-01-01
forum: General Help
---

### Post by skelooth on 2007-01-01
This has been an issue from the very beginning of a vanilla edgy install. Totem does not play mp3s or mpgs or anything of that nature, yet firefox was trying to use it as a media plug (Might I add I think that's pretty pointless?). So I go rid of the symbolic link in firefoxes plug in directory .... to no avail. I uninstalled and reinstalled the vlc mozilla plug in... still to no avail.

Anytime there is an embed, or I click on a movie, it just says "no image available" and nothing else. It doesn't matter what type of media it is either.

---

### Post by bruenig on 2007-01-01
Try mozilla-mplayer. Plays pretty much everything.

---

### Post by rajeev1204 on 2007-01-01
hi

yes , i agree

mozilla-mplayer will play everything.


regards

rajeev

---

### Post by skelooth on 2007-01-01
> **rajeev1204 said:**
> hi

yes , i agree

mozilla-mplayer will play everything.


regards

rajeev

no go. I sudo apt-get installed it, restarted firefox. Same issue. it just says (no video) and never actually loads anything (load bar insta-finishes) but if I download to my desktop it works fine in vlc.

---

### Post by bruenig on 2007-01-01
You need to remove all the other things.
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc
```

Also, make sure you have all the codecs installed.

---

