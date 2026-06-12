---
title: "Installing ATI Radeon 9800 Pro Drivers"
date: 2008-01-01
forum: General Help
---

### Post by m i k e on 2008-01-01
I just downloaded the newest drivers for this card from the ATI site.  They seem to only officially support it on RedHat and Suse.  Will the automatic install work fine for Ubuntu or is there something I should do to increase compatibility?

---

### Post by tgilber1 on 2008-01-02
The proprietary drivers should work fine.  It will probably load a kernel object module named fglrx.  You can verify that it's loaded by using modprobe -l fglrx, which provides the module's absolute path.  

Lastly, to load proprietary drivers, you will have to edit the /etc/default/linux-restricted-modules-common by adding fglrx to the DISABLED_MODULES line to enable your system to load the proprietary rather than its own driver.

DISABLED_MODULES="fglrx"

---

### Post by m i k e on 2008-01-02
So the general consensus would be to use the proprietary driver even though it is listed under "Restricted Drivers"?

See screenshot:  [http://img85.imageshack.us/img85/3070/atidriverzl0.jpg](http://img85.imageshack.us/img85/3070/atidriverzl0.jpg)

---

