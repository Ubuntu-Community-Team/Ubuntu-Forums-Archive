---
title: "Getting driver to run on boot"
date: 2008-02-23
forum: General Help
---

### Post by madkid on 2008-02-23
Hello everyone. I have a driver that I need to load on boot up in Ubuntu 7.04. I know that I can use System>Preferences>Sessions to do this, but I need to know how to make my admin password work without needing to put it in manually. Is there a way to do this?

---

### Post by pointone on 2008-02-23
If you need something to run as root during boot, run it from "/etc/rc.local".

---

### Post by shad0w_walker on 2008-02-23
I assume this is a module you need to load, if so I refer to you to this thread, which shows how to load a module at boot up.

[http://ubuntuforums.org/showthread.php?t=705916](http://ubuntuforums.org/showthread.php?t=705916)

---

