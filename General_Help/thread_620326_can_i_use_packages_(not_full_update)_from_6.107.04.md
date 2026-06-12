---
title: "can i use packages (not full update) from 6.10/7.04/7.10 repos on dapper?"
date: 2007-11-22
forum: General Help
---

### Post by erlinux on 2007-11-22
can i use packages (not full update) from 6.10/7.04/7.10 repos on dapper?
like installing ice tea java, xfce 4.4.1, synaptic, basic utilites and software?

---

### Post by jaspreet on 2007-11-22
sure you can. best way would be by downloading synaptic package manager's deb package and installing it. After that you can install any desired package from synaptic itself!

---

### Post by bodhi.zazen on 2007-11-22
you can, but you may have problems ...

You can download a .deb and install with 

```
sudo dpkg -i <package_name
```

If you want to use apt-get / syanptic you need to "pin"

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

