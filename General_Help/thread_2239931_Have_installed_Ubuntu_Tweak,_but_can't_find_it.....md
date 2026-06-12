---
title: "Have installed Ubuntu Tweak, but can't find it...."
date: 2014-08-16
forum: General Help
---

### Post by gabmuks on 2014-08-16
Hello and good day

Have installed Ubuntu Tweak but can't find it anywhere.

How can I use a terminal to run Ubuntu Tweak?


Thanks for your time.

---

### Post by Frogs Hair on 2014-08-16
```
 ubuntu-tweak
``` Some of the settings are Unity specific.

---

### Post by monkeybrain20122 on 2014-08-16
It is probably in Settings. There is a bug in xfce apparently so some applications don't show up in the menu but only in Settings, e.g gparted. Since Ubuntu-tweak is a system tool it may be there as well.

---

### Post by vasa1 on 2014-08-16
I'm not sure it's a good idea for a Xubuntu user to run Ubuntu Tweak because I'm not sure it's a "cross-flavor" application. Anyway, I've never used it.

Could you please post the output of the corresponding **.desktop** file (excluding all the translations!). It should be in **/usr/share/applications**. I feel there may be a line like **OnlyShowIn=***;** or **NotShowIn=***;** which makes it "invisible" to XFCE users.

BTW, [https://answers.launchpad.net/ubuntu-tweak/+faq/751](https://answers.launchpad.net/ubuntu-tweak/+faq/751) seems to have been last updated on **2009-10-13**! Anyway, the page visible to me has:
> At present, It is only designed for Ubuntu GNOME Desktop, and often follows the newest Ubuntu distribution.

---

