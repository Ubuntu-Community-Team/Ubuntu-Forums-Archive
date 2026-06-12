---
title: "how to get webmin to work on Ubuntu"
date: 2004-11-16
forum: General Help
---

### Post by wayover13 on 2004-11-16
Webmin is that nice system control interface that displays in your web browser.  Might seem like a really simple thing to get it going on Ubuntu: it is, after all, in the repository (it's in universe, at least--not sure if it shows up if you didn't add universe to your repository list).  Seems like all you might have to do is select it in Synaptic, click "apply" and go!  But there's a problem.  Webmin expects to be run by the root user on the system.  Since Ubuntu uses sudo for root/superuser tasks, there is no root password (although there is a root user: all you Ubuntu developers can now speak up and tell us what password NSA told you to assign to root :) ).  Therefore, if you install webmin without assigning root a password, you won't be able to log in and use it.  It will not accept your user's password.  So, if you want to install webmin, assign root a password FIRST: sudo passwd root.  After you've assigned root a password in this way you can install webmin and log in as root.  Then you can assign your user whatever priviledges you want so you don't have to keep logging in as root.

James

---

### Post by FLeiXiuS on 2004-11-16
**Moved to general support**

Please read [http://ubuntuforums.org/showthread.php?t=3512](http://ubuntuforums.org/showthread.php?t=3512) before posting in the HOWTO / FAQ section.

---

