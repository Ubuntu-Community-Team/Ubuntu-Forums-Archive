---
title: "New software can't be installed... error"
date: 2016-04-11
forum: General Help
---

### Post by kd8tzc on 2016-04-11
Hi all, I'm new to Ubuntu so I hope someone can help me.  I recently was installing Dolphin, and it generated an error while installing.  

When trying to use the Fix within the GUI application, I get the following details.
```

Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.10.20150723-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of kde-telepathy:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.20ubuntu1); however:
  Package kde-telepathy-minimal is not configured yet.


dpkg: error processing package kde-telepathy (--configure):
 dependency problems - leaving unconfigured



```

Can someone tell me how I resolve this?  I tried apt-get -f install, but that didn't help.

I am running Ubuntu 15.10.

Thanks

---

### Post by oldos2er on 2016-04-11
Looks like there may be a solution [here]("http://askubuntu.com/questions/693735/broken-package-error-when-trying-to-install-kubuntu-desktop-in-ubuntu-15-10").

---

