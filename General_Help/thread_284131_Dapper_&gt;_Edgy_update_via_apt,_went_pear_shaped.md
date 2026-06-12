---
title: "Dapper &gt; Edgy update via apt, went pear shaped"
date: 2006-10-25
forum: General Help
---

### Post by Morrolan on 2006-10-25
Hi,
   Last night I decided to upgrade from Dapper to Edgy RC1 via APT.  I don't know if this matters, but I didn't exit gnome, I left the login screen running on CTRL+ALT+F7, but went to CTRL+ALT+F2, logged in, and ran the following after changed my sources.list and replacing "dapper" with "edgy":

```
sudo apt-get update && sudo apt-get install ubuntu-desktop && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```As instructed at [https://wiki.ubuntu.com/EdgyUpgrades]("https://wiki.ubuntu.com/EdgyUpgrades").

After that, I got a message saying that my xserver wasn't configured correctly - 'dpkg-reconfigure xserver-xorg' swore blind it was fine, apt said it was held back, so once I'd updated it using apt, I got X running.

ISSUE:
I now get an error message saying that my login manager keeps crashing, so it will use another one.  I end up using the X login manager (ugly) and I can get in.  I then get an error message saying that my processor doesn't support freq. scaling - I know it doesn't, why doesn't Ubuntu?

What I would like help with is:

1.  Did I do anything wrong?
2.  Where should I start looking to rebuild/reconfigure the login manager?
3.  How can I stop ubuntu telling me that my CPU doesn't support frequency scaling every time I boot?

Many thanks in advance,
Morrolan

---

### Post by pay on 2006-10-25
I prefer to use aptitude to upgrade/install meta packages but apt-get should do the same thing. Maybe gdm wasn't installed after the upgrade try "sudo aptitude install gdm" or something along those lines, I'm not entirely sure what the package is called. Also I think that it is always better to do a clean install of Ubuntu when a new release is out, but thats just me.

---

