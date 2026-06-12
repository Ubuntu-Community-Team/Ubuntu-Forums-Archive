---
title: "X won't start after java install"
date: 2005-07-15
forum: General Help
---

### Post by Maxkekaxke on 2005-07-15
I installed the java jre-1_5_0_04-linux-i586.bin and installed it like it is explained on [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)
I installed the latest Eclipse 3.1 version too...

When I reboot my ubuntu, X won't start anymore!
Is this a well-known issue? Or what can I do to solve this?
I can't simply uninstall the bin (I think)...

Thanks!

---

### Post by zlogic on 2005-07-15
[QUOTE=Maxkekaxke]I installed the java jre-1_5_0_04-linux-i586.bin and installed it like it is explained on [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)
I installed the latest Eclipse 3.1 version too...

When I reboot my ubuntu, X won't start anymore!
Is this a well-known issue? Or what can I do to solve this?
I can't simply uninstall the bin (I think)...

Thanks![/QUOTE]
 I've installed that version of Java, and I think it doesn't do any system-wide configuration. You don't have to be root to install it. You can install Java into ANY directory and it will work from there. So I think it's something else...
Try typing "sudo dpkg-reconfigure xserver-xorg" to automatically create a new configuration file for X.

---

### Post by Maxkekaxke on 2005-07-15
thx, but that doesn't make it work :neutral:
maybe any other solutions?

---

