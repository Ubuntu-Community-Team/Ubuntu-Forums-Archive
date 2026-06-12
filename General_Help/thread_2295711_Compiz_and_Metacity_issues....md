---
title: "Compiz and Metacity issues..."
date: 2015-09-20
forum: General Help
---

### Post by Nixarter on 2015-09-20
I apparently have metacity as my default (window manager?), but I would like compiz.  I have the compiz config settings manager all up and running... but when I try ```
compiz --replace
``` my min/max buttons disappear, and a lot of things don't work so well.  I thought I bricked the install for a minute :o  Then I ran ```
metacity --replace
``` and everything is back to normal.

Is compiz --replace not the correct way to start it?  I've used it a long time ago, but I've forgotten how to do it properly.  Every video and instruction I can find, it magically does it itself while going through the CCSM, but I can't get it to do anything unless I type compiz --replace, so I'm obviously missing something somewhere.

---

### Post by Nixarter on 2015-09-20
```
$ compiz --replace
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: wobbly
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Loading plugin: cube
compiz (core) - Info: Starting plugin: cube
compiz (core) - Info: Loading plugin: rotate
compiz (core) - Info: Starting plugin: rotate
compiz (core) - Info: Loading plugin: cubeaddon
compiz (core) - Info: Starting plugin: cubeaddon
compiz (cubeaddon) - Warn: Failed to load slide: fusioncap.png
compiz (cubeaddon) - Warn: Failed to load slide: compizcap.png
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: td
compiz (core) - Info: Starting plugin: td
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct

```

i tried it again, and read the output.  maybe I just need to define a couple more parameters and try again...

---

### Post by grahammechanical on 2015-09-20
Compiz and Metacity do similar things. We run with one or the other. So, if you are running with a metacity session then the command compiz --replace would be the wrong command to run. Likewise if we was runing with a Compiz session we would not run the command metacity --replace.

You have not told us what version of Ubuntu your are using. A default install of Ubuntu would only have Compiz as the compositing/window manager. Metacity would not be installed. On the other hand, if we install gnome-session-flashback we get to 2 extra sessions at the login screen. a) Ubuntu; b) Gnome Flashback (Compiz); c) Gnome Flashback (Metacity). This would be with Ubuntu 15.04.

Perhaps you are using Ubuntu Mate. I am not sure if that gives the user an option to choose at the login screen whether to use Compiz or Metacity. I think it does but I am not sure. Anyway, it would help if you told us the Ubuntu version or flavour of Ubuntu, do you not think so? Are you still on 12.04? Did you install Unity 2D?

We select the session at the login screen and the last used session becomes the default.

Regards.

---

### Post by ajgreeny on 2015-09-21
> **grahammechanical said:**
> Compiz and Metacity do similar things. We run with one or the other. So, if you are running with a metacity session then the command compiz --replace would be the wrong command to run. Likewise if we was runing with a Compiz session we would not run the command metacity --replace.
If I remember correctly, I think you have got that the wrong way round.

It is a long time since I used either compiz or metacity, but I know that when I was running a Ubuntu gnome 2 desktop and wanted to replace compiz with metacity as window manager I used exactly the command you say is incorrect, ie, ```
metacity --replace
```
Things may have changed as the Ubuntu versions and packages versions have matured, but we need to double check this.

You may also need to open the compizconfig-settings-manager to double check that the window-decoration plugin is enabled.

---

