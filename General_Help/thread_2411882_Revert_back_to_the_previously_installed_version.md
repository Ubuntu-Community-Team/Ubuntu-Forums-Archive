---
title: "Revert back to the previously installed version"
date: 2019-02-05
forum: General Help
---

### Post by jek1 on 2019-02-05
Ubuntu 14.04 LTS

Is there any way that one can revert back to the previously installed version of a software application if you are not happy with the latest upgrades? For example like a System Restore in Windows.

---

### Post by TheFu on 2019-02-05
In Unix/Linux, "system restore" is called "backups".  So, you can restore from a backup made prior to the change, assuming you made a backup previously. They are not automatic.

If you don't want a specific package to be upgraded, you can put a "hold" on it using APT.  While this will prevent that specific package from being updated, it will also prevent any specific dependencies from being upgraded too. This might be exactly what you want or it might lead to multiple added attack vectors.  
```
$ sudo apt-mark hold {package-name}
```
so something like 
```
$ sudo apt-mark hold mysql-server
```

Since support for 14.04 will be ending in a few months, provided the system is not on an internet connected network, I wouldn't worry about these risks much.  If the system is connected to the internet, I'd be very concerned and would want to know all the dependencies being held back. I think the **ubuntu-support-status** command should show that with a few options.

For example, I see that my apache2 package isn't supported any longer. If that system was available to the internet, I'd be freaking out!  It is not, so I'm much less worried.  I don't have a "hold" on apache2, BTW. Non-core packages loose support over time.

---

### Post by jek1 on 2019-02-05
Thanks TheFu. I don't want to prevent any software from being upgraded,  but if it is upgrade and I am not happy with the upgraded software, I  would like the option to revert back to before the upgrade. So backus  would be the answer then, but what exactly must I then backup and  restore to undo the upgrade?

---

