---
title: "Gutsty+xgl+(compiz start)"
date: 2007-11-22
forum: General Help
---

### Post by TechMansoor on 2007-11-22
My machine has been busted up and nothing is working correctly. Tried to get the default compiz-fusion or compiz that comes with gutsy to start(compiz start via  konsole terminal) and everything is wacked. Even if I reboot nothing works correctly and goes back to doing what its doing. It noted that XGL wasn't present when I tried compiz start. I got system monitor to pull up and noticed xgl was running in the background.

My questions are:

How do I get back to where compiz and xgl never was running?

Is there a restore function in gutsy similar to windows?


Things ive tried:

I've tried restoring the xorg.conf file to a backup I previously made but nothing happened. Can anyone help please?

Thanks

---

### Post by Forlong on 2007-11-22
> **TechMansoor said:**
> How do I get back to where compiz and xgl never was running?
The easiest way would be removing Xgl:
```
sudo apt-get remove xserver-xgl
```

---

### Post by TechMansoor on 2007-11-22
> **Forlong said:**
> The easiest way would be removing Xgl:
```
sudo apt-get remove xserver-xgl
```

Yep that did it.Copied over the backed up xorg file and everything is cool again. I think im gonna leran everything about linux and ubuntu then give compiz-fusion a try again. I'll start with a practical guide to linux...seems to be awesome..

Thanks a million

---

