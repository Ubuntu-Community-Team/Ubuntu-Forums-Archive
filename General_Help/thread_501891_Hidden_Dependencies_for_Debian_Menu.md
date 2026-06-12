---
title: "Hidden Dependencies for Debian Menu?"
date: 2007-07-15
forum: General Help
---

### Post by jusmurph on 2007-07-15
I installed the Debian Menu (using automatix) a while ago as I had some programs racking up that where not getting a mention normally and it would not take long for me to forget the fact that I even had them let alone the command. It never worked and it did a quick search of the forums with no luck and didn’t really bother, last night I installed a few games via apt-get and went to launch them and the Debian menu was there!

So what was the issue before that seemingly has corrected itself?

---

### Post by RedSquirrel on 2007-07-16
I'm not sure. Something you installed must have updated the menu. In any case, assuming the menu package is installed, all you should have to do to generate the Debian menu is:

```
sudo update-menus
```

---

