---
title: "win4lin gtk"
date: 2007-04-25
forum: General Help
---

### Post by jrock2004 on 2007-04-25
ok installed win4lin pro and when starting nothing happens. I start it from command line and get this error

```

johnc@Desktop:~$ winpro /opt/win4linpro/bin/mergepro-gmsg: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Ubuntu 7.04 is what I am running

What should I do here?

---

### Post by williamrice on 2007-04-29
Before installing win4lin, you must install libgtk1.2. First, make sure you have enabled the Universe repository in Synaptic. Then close Synaptic, and in a terminal window, do this:
sudo apt-get update
sudo apt-get -y install ibgtk1.2
linux-headers-$(uname -r) gcc

You should have done this before installing win4lin. However, since you've already installed win4lin, I hope that you don't need to uninstall it and then do this.

---

