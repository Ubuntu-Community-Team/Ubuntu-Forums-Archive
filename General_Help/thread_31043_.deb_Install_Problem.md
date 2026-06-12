---
title: ".deb Install Problem"
date: 2005-05-01
forum: General Help
---

### Post by Briggzee on 2005-05-01
I'm trying to install VLC using some .deb files on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And I've been working my way through the dependencies, except now I am stuck.
When I try and install VLC  I get;

**$ sudo dpkg --install vlc_0.8.1-1ubuntu7_amd64.deb**

(Reading database ... 66164 files and directories currently installed.)
Preparing to replace vlc 0.8.1-1ubuntu7 (using vlc_0.8.1-1ubuntu7_amd64.deb) ...
Unpacking replacement vlc ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on wxvlc; however:
  Package wxvlc is not configured yet.
dpkg: error processing vlc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vlc

Then when I try and and install the depdencie it asks for (wxvlc)  I get;

**$ sudo dpkg --install wxvlc_0.8.1-1ubuntu7_amd64.deb**

(Reading database ... 66164 files and directories currently installed.)
Preparing to replace wxvlc 0.8.1-1ubuntu7 (using wxvlc_0.8.1-1ubuntu7_amd64.deb) ...
Unpacking replacement wxvlc ...
dpkg: dependency problems prevent configuration of wxvlc:
 wxvlc depends on vlc (= 0.8.1-1ubuntu7); however:
  Package vlc is not configured yet.
dpkg: error processing wxvlc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wxvlc

Seems like they are dependant on each other, I cant figure out how to install them.
Any suggestions?

---

### Post by cutOff on 2005-05-01
i'm not sure if it will work but you can try

```
$ sudo dpkg -i *.deb
```

---

### Post by Briggzee on 2005-05-01
[QUOTE=cutOff]i'm not sure if it will work but you can try

```
$ sudo dpkg -i *.deb
```[/QUOTE]
 Worked like a charm.

Thanks a lot.

---

