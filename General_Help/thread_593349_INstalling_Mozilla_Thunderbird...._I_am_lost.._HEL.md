---
title: "INstalling Mozilla Thunderbird.... I am lost.. HELP!!"
date: 2007-10-27
forum: General Help
---

### Post by eric5279 on 2007-10-27
So what I have done so far is downloaded the program to my desktop and the folder is called "thunderbird-2.0.0.6.tar.gz".  BUt what do I do now?  I am lost.  Please help I need to get my EMail back up ASAP.  THanks.

---

### Post by taurus on 2007-10-27
What's wrong with the one from the repos?

System -> Administration -> Synaptic Package Manager -> Search -> mozilla-thunderbird

Otherwise, open a terminal and do

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf thunderbird-2.0.0.6.tar.gz
cd thunderbird-2.0.0.6
```
and there should be a thunderbird program that you can run from there.

```
./thunderbird
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

