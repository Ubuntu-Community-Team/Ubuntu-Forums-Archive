---
title: "can't find FrostWire after removing from Synaptic Packet Manager"
date: 2008-02-06
forum: General Help
---

### Post by FastMady123 on 2008-02-06
I uninstalled FrostWire because it dosn't work when I click on It. In Synaptic, after I removed, I can't find FrostWire because I remove it. Is FrostWire in Synaptic gone forever? What should I do to bring FrostWire back to Synaptic?

---

### Post by FuturePilot on 2008-02-06
It's not in the repositories so it's not going to show up. You'll have to redownload it from Frostwire's website.

---

### Post by Rocket2DMn on 2008-02-06
Frostwire is not in the repositories, but you can download the .deb file from [http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads) and it will show in synaptic afker you install.
You can install by double clicking the .deb file or running
```
cd /path/to/downloaded/file
dpkg -i frostwire-4.13.4.i586.deb
```

---

### Post by luctor on 2008-02-06
> **FastMady123 said:**
> I uninstalled FrostWire because it dosn't work when I click on It. In Synaptic, after I removed, I can't find FrostWire because I remove it. Is FrostWire in Synaptic gone forever? What should I do to bring FrostWire back to Synaptic?

Frostwire doesn't work well with the default java version installed with Ubuntu.
It got it working with ia32-sun-java6-bin package.

---

