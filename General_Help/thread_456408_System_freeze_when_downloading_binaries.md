---
title: "System freeze when downloading binaries"
date: 2007-05-27
forum: General Help
---

### Post by Acknud on 2007-05-27
I am having problems downloading binaries.  I have setup and used klibido, hellanzb and grabit under wine.  They all work well and do what they are supposed to.  My problem is they all freeze up my system after an unspecified amount of time.  It may be 2 minutes or 2 hours.  It seems to be random.  

I use Giganews and have tried no other but I can't see my newsserver causing a system lockup.  Anyone experiencing this or have any ideas?

---

### Post by Acknud on 2007-06-10
Anybody out there?  Surely someone knows something about this problem!?

---

### Post by jwh400 on 2007-06-10
If they're all doing it then it may be a Wine problem. Have you tried Pan newsreader? It's available in your repositories and of course won't require Wine.

---

### Post by Acknud on 2007-06-12
Thanks for the reply.  I don't see how it can be wine when klibido and hellanzb lock up as well.  I looked at Pan before but I never could get it to work with nzbs.

---

### Post by hardwarehank on 2008-01-26
I have seen this same exact problem!  I can reproduce it by just running hellanzb with giganews through my stunnel4 redirect.  It is also an unspecified amount of time for me.  What kind of system are you running?  Here are my specs:

* Core2Duo E6300
* 2GB of Mushkin DDR2-800
* Gigabyte 965P Motherboard

I have replaced bad RAM to diagnose this, but it doesn't help.  I have also replaced bad SATA cables, but when it crashes I can check /proc/mdstat and find that the RAID hasn't degraded, so that's not it.  I believe it has something to do with the JMicron SATA controller.  Post your system hardware and we'll see if we have any similarities.

---

