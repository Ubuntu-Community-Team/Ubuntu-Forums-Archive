---
title: "how to &quot;uninstall&quot;"
date: 2005-07-16
forum: General Help
---

### Post by Vetto on 2005-07-16
ok.  How do I remove a library (libusb) that was installed by "make install" vs a debian package or apt-get?

is there a "make uninstall"?  

And if there is, how can I be assured that it wont remove files that are needed by the older version of the lib that is still installed?

---

### Post by Xian on 2005-07-17
[QUOTE=Vetto]How do I remove a library (libusb) that was installed by "make install" vs a debian package or apt-get?

is there a "make uninstall"? [/quote]
You open a terminal and cd back to the source path.
Then you issue a 'sudo make uninstall' command

[QUOTE=Vetto]And if there is, how can I be assured that it wont remove files that are needed by the older version of the lib that is still installed?[/QUOTE]
You'd have to reinstall the older lib to be certain.

---

### Post by Vetto on 2005-07-17
make uninstall?? :eek:   Why is it always so easy... 

Will try that in the morning.

---

