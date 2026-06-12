---
title: "Today's updates broke kde-window-manager"
date: 2013-08-14
forum: General Help
---

### Post by deadtom on 2013-08-14
I updated today, nothing special. Just ran apt-get update, then rebooted and now kde-window-manager is broken.

I have no idea how to fix this. Here is a snippet from me trying to get it installed:


```
$ sudo apt-get install kde-window-managerThe following packages have unmet dependencies:
 kde-window-manager : Depends: libgles2-mesa (>= 7.8.1) but it is not going to be installed or
                               libgles2
                      Depends: libkwinglesutils1 (= 4:4.11.0-0ubuntu1~ubuntu13.04~ppa1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
$ sudo apt-get install libgles2-mesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
 libgles2-mesa : Depends: libglapi-mesa (= 9.1.4-0ubuntu0.1) but 9.2.0~git20130729+9.2.9b8ad643-0ubuntu0sarvatt~raring is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

