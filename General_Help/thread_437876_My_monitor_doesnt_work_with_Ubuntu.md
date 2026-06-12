---
title: "My monitor doesnt work with Ubuntu?"
date: 2007-05-09
forum: General Help
---

### Post by dcskater_12 on 2007-05-09
I have two brand new 17" aceral1706's and a really old 15" crt made in 1998. The two flatscreens (the acers) are setup side by side for video editing and are running off a windows computer. The crt is what i hoped to use for ubuntu, but the screen just goes black when i try. the acers work with ubuntu but not the crt? is it resolution problems or is the monitor just not good enough? Please help!!

---

### Post by denver on 2007-05-09
Its most likely a resolution problem. Try the following:

```
control+alt+F1
```
```
dpkg-reconfigure -phigh xserver-xorg
```

the second command wil automaticaly reconfigure your xorg.conf. if you wish to go through it step by step use:

```
dpkg-reconfigure xserver-xorg
```

Hope this helps. Good luck!

---

