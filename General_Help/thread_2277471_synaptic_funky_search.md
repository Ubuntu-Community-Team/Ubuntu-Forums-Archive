---
title: "synaptic funky search"
date: 2015-05-09
forum: General Help
---

### Post by monkeybrain20122 on 2015-05-09
Does anyone notice that synaptic is kind of behaving strangely in 15.04? It often (not always) takes an unusually long time for quick filter to "rebuild search index" and then often it doesn't find packages? e.g I couldn't find curl  in synaptic (only libcurl shows up) but sudo apt-get install curl works

---

### Post by Frogs Hair on 2015-05-09
I noticed some strange behaviour the first day, the quick filter was opening as a separate window, but all was normal the next day. I did find curl which was needed for conky weather.

---

### Post by monkeybrain20122 on 2015-05-11
No one else is having issues with searching and rebuilding search index?

---

### Post by monkeybrain20122 on 2015-05-13
This happens sporadically, sometimes it doesn't find things.. for example, if I click qt and look at the 'uninstall' section it is empty (certainly I did not install all qt packages) and then restart synaptic and the section is full. Sometimes 'rebuilding search index' takes a long time I just kill it, then restart and it seems normal. It is as though it has problem finding the server. I switched server from main to Canada and then back  a few time the problem persists, but not always, only kind of on and off.

Does anyone have the same experience. I know a lot of people use synaptic it would be odd that this only happens to me (it is a clean install, not even an old /home partition)

---

### Post by monkeybrain20122 on 2015-05-21
Well I am not crazy, something is wrong and I have figured it out. Got hit by something going back to "jaunty" [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

Same fix works. 

```
sudo update-apt-xapian-index
```

It has been a day since I ran this command and have rebooted a dozen of times, synaptic has been working normally and consistently so I am marking this thread as solved.

---

