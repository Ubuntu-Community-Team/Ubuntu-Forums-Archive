---
title: "file-roller and xarchiver"
date: 2015-01-11
forum: General Help
---

### Post by nep-nori on 2015-01-11
Hello everyone. Very recently I tried to build up a working DE from the netboot mini.iso and I was successful for the most part; however, there are some seemingly redundant apps I got through dependencies probably.

Long story short, since I have both file-roller and xarchiver installed,  can I safely axe either one without missing functionality? as in, do they do the exact same things?

furthermore, which one should I nuke? if one were to get nuked in the first place...

---

### Post by mörgæs on 2015-01-11
Why do you want to remove one? The hard disk space you save is so small that you will not notice the difference.

---

### Post by nep-nori on 2015-01-11
> **mörgæs said:**
> Why do you want to remove one? The hard disk space you save is so small that you will not notice the difference.

my comp is a glorified toaster, hence my desire (and need?) to built up a fully-functional DE that is also completely free of things I don't use. 2 file-managers qualify as things you won't ever need, because 1 is enough.

---

### Post by nerdtron on 2015-01-11
Sure you can remove one as long as the other is does what you want it to do.

---

### Post by ibjsb4 on 2015-01-12
My last toaster had 256M of ram and a 20G HDD.
> there are some seemingly redundant apps
You can get around some of those redundant apps by using "no-install recommends".  Example:
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```
Will leave off all the recommends. 
[http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop)

This works on any package that has recommended packages.

---

### Post by nep-nori on 2015-01-12
> **ibjsb4 said:**
> My last toaster had 256M of ram and a 20G HDD.

You can get around some of those redundant apps by using "no-install recommends".  Example:
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```
Will leave off all the recommends. 
[http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop)

This works on any package that has recommended packages.

I knew about --no-install-recommends already but thank you. From what I've gathered so far, in my specific case xarchiver comes as a recommended package of one of another package's dependency (do those even install by default? apparently for me they do).

Anyway, I nuked file-roller and everything's working fine. Thread marked as solved.

---

