---
title: "install .deb and see list of unsatisfied dependencies"
date: 2020-01-18
forum: General Help
---

### Post by shmu26 on 2020-01-18
On Kubuntu 19.10, I am trying to install a .deb file, it is an older version of VirtualBox (5.2), and I am getting an error message that there are unsatisfied dependencies. But even if I run it from terminal, I don't get a list of those dependencies. How can I get the list, so I can troubleshoot the problem?

---

### Post by Dennis N on 2020-01-18
Try using **gdebi** package installer. As I recall it showed specifically what is wrong if there are problems with dependencies or other conflicts.

---

### Post by shmu26 on 2020-01-18
Gdebi is great, I use it on other distros, but it won't launch for me on Kubuntu.

---

### Post by coffeecat on 2020-01-18
> **shmu26 said:**
>  How can I get the list, so I can troubleshoot the problem?

In a terminal, cd to the directory your virtualbox*.deb file is in, and:

```
dpkg-deb -I virtualbox*.deb
```

You will see information about the package, including a list of dependencies. If you want a text file to read at your convenience:

```
dpkg-deb -I virtualbox*.deb > textfile
```

Change "textfile" to whatever you want.

---

### Post by SeijiSensei on 2020-01-18
There's a build of 5.2 at Oracle for 18.04 thru 19.04.  I bet it will work on 19.10 as well.

[https://download.virtualbox.org/virtualbox/5.2.36/virtualbox-5.2_5.2.36-135684~Ubuntu~bionic_amd64.deb](https://download.virtualbox.org/virtualbox/5.2.36/virtualbox-5.2_5.2.36-135684~Ubuntu~bionic_amd64.deb)

Is this the one you tried to install?

See: [https://www.virtualbox.org/wiki/Download_Old_Builds_5_2](https://www.virtualbox.org/wiki/Download_Old_Builds_5_2)

---

