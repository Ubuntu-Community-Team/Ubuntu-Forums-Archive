---
title: "[SOLVED] &amp;quot;Package pidgin is not installed, so not removed&amp;quot;"
date: 2008-02-19
forum: General Help
---

### Post by SomeGuyDude on 2008-02-19
I installed Pidgin via source, and now I cannot uninstall it (problem with the Pidgin Screenlet, I'd like to start from scratch). It's not in Synaptic, and "sudo apt-get remove pidgin" yields this:

```
crew@crew-laptop:~/pidgin-2.3.1$ sudo apt-get remove pidgin
[sudo] password for crew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
crew@crew-laptop:~/pidgin-2.3.1$
```

I may have used "./configure --prefix=/usr" when I installed it, could that have muffed things up? If so, how can I fix it? For that matter, if NOT, how can I fix it? :confused:

---

### Post by amingv on 2008-02-19
When you installed it, did you use sudo make install or sudo checkinstall?

If you used make install, try browsing to the directory where the source is and type
```
sudo make uninstall
```

To make life easier in the future, you can use checkinstall instead of make install:
```
sudo apt-get install checkinstall
```

---

