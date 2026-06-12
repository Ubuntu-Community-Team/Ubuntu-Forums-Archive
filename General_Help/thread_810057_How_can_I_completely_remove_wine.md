---
title: "How can I completely remove wine?"
date: 2008-05-27
forum: General Help
---

### Post by OMRebel on 2008-05-27
I'm running Ubuntu 8.04.  I had installed Wine a couple of Windows apps.  However, I want to completely remove those apps and wine.  I tried uninstalling the applications using the Uninstall feature in wine, but it kept those apps there.  So, I went to remove wine using Synaptic, but wine still shows up.  How can I completely remove wine from my system?

Thanks.

---

### Post by strabes on 2008-05-27
```
sudo aptitude purge wine
```

Remove the menu (if it is not automatically removed) using System > Preferences > Main Menu.

---

### Post by bodhi.zazen on 2008-05-28
```
sudo apt-get remove --purge wine && rm -rf ~/.wine
```

---

