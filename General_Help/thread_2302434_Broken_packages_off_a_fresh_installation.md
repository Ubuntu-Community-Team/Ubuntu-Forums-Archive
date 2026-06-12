---
title: "Broken packages off a fresh installation"
date: 2015-11-10
forum: General Help
---

### Post by vperaino on 2015-11-10
This is twice I've installed Xubuntu fresh now that I'm getting broken packages shortly after installation. 

The offending packages are as follows: 

```
[FONT=arial]The following packages have unmet dependencies:[/FONT]
[FONT=arial] cairo-dock : Depends: cairo-dock-plug-ins (>=[/FONT]
[FONT=arial]3.3.99.beta1.2.really.3.3.2) but it is not going to be installed[/FONT]
[FONT=arial]              Depends: cairo-dock-plug-ins-dbus-[/FONT][FONT=arial]interface-python (>=[/FONT]
[FONT=arial]3.3.99.beta1.2.really.3.3.2) but it is not going to be installed[/FONT]
[FONT=arial] kdiff3 : Depends: kde-runtime but it is not going to be installed[/FONT]
[FONT=arial]          Depends: libkdecore5 (>= 4:4.4.4) but it is not going to be installed[/FONT]
[FONT=arial]          Depends: libkdeui5 (>= 4:4.4.4) but it is not going to be installed[/FONT]
[FONT=arial]          Depends: libkio5 (>= 4:4.5.85) but it is not going to be installed[/FONT]
[FONT=arial]          Depends: libkparts4 (>= 4:4.5.85) but it is not going to be installed[/FONT]
[FONT=arial] python-pip : Depends: python-setuptools (>= 0.6c1) but it is not[/FONT]
[FONT=arial]going to be installed[/FONT]
[FONT=arial]              Recommends: build-essential but it is not going to be installed[/FONT]
[FONT=arial]              Recommends: python-dev-all (>= 2.6) but it is not installable[/FONT]
[FONT=arial] rst2pdf : Depends: python-setuptools but it is not going to be installed[/FONT]
[FONT=arial]E: Unable to correct problems, you have held broken packages.[/FONT]
```

I have no problems installing/updating these packages on a second machine. Trying to follow the dependency trail leads to, predictably, an infinite regress of dependencies. Clean, autoremove, and force-install have no effect. 

What do I do when this happens?

---

### Post by ian-weisser on 2015-11-10
You seem to have a version conflict.
Here's an example picked at random: 
> [FONT=arial] kdiff3 : Depends: kde-runtime but it is not going to be installed[/FONT] [FONT=arial]          Depends: libkdecore5 (>= 4:4.4.4) but it is not going to be installed[/FONT] [FONT=arial]          Depends: libkdeui5 (>= 4:4.4.4) but it is not going to be installed[/FONT]

Guess what: libkdeui5 4:4.4.4.4 isn't in the Ubuntu repos. Other versions are, but not that one.
So whatever you're trying to install, it seems to be from a non-Ubuntu source that's *way* behind the times.

What can you do? Install from the tested, safe, secure Ubuntu repos, of course, instead of wherever on the dirty, dirty internet you are going now.

---

