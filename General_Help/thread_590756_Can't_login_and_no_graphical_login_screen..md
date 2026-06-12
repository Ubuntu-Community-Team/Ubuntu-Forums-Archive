---
title: "Can't login and no graphical login screen."
date: 2007-10-25
forum: General Help
---

### Post by dopefish124 on 2007-10-25
Hello.
I've been using Ubuntu for a few months now and, yeah, it's been very good :D. But a while ago, more than two weeks, something awful happened to my system. Now when I start up Ubuntu I get a scrolling screen full of information about what the computer is doing as it starts Ubuntu (I've seen this on other Linux distros before). Of course, Ubuntu doesn't usually do this. Also, with my non-graphical login screen I can't login to any user accounts except root and that's dangerous, right? When I try to login to a normal account it says "cannot cd to /home/[username]".
I'll post more details if necessary.
Thanks! ;D

---

### Post by Qwerty_ on 2007-10-25
I am not sure whats going on with your login account problem however a simple command should hopefully fix up your graphicial issues.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dopefish124 on 2007-10-25
Okay, super. It's probably unlikely but maybe I'll be able to login when the graphical login screen comes back.

EDIT: I tried it and didn't work, dang. I'm thinking now that maybe I should reinstall Ubuntu. Is that possible without destroying my current files?

---

### Post by taurus on 2007-10-25
What are the outputs of these command from a prompt?

```
df -h
ls -la /home
```

---

### Post by dopefish124 on 2007-10-27
Thank you all for your help but I'm take the easier, less efficient way out and give Ubuntu a reinstall. This is just too difficult for me.

---

