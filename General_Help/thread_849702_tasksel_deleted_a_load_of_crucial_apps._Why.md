---
title: "tasksel deleted a load of crucial apps. Why?"
date: 2008-07-04
forum: General Help
---

### Post by KenBW2 on 2008-07-04
I used tasksel to remove all packages related to LAMP Server. I watched the progress bar at about 20% and it was uninstalling music-applet and fast-user-switcher. I quickly closed Terminal to stop it uninstalling anything more that I needed.

I reemerge to find that it's uninstalled a plethora of crucial apps, including:
- Nautilus
- Adobe Reader
- XPdf
- *ubuntu-desktop*

Every time I install an application it tells me
```

The following packages were automatically installed and are no longer required:
  python-crypto libical0 libbtctl4 python-paramiko bitpim-lib libgnokii3
  python-dsv libpcsclite1 python-serial libmcrypt4 dasher-data python-ctypes
  python-apsw python-wxversion gnokii-common libgnomebt0 python-wxgtk2.6

```

I found out that I can look at /var/log/dpkg.log to see what it's done. Frankly I'm baffled and mortified by what's gone and am currently undergoing the painful process of reinstalling stuff.

Why did it do this? And what would've become of my computer had I left it to finish?

---

### Post by KenBW2 on 2008-07-04
*bump* 

(sorry)

---

