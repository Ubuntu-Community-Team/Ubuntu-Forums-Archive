---
title: "Finding info on terminal of package before install"
date: 2013-07-09
forum: General Help
---

### Post by and0rsk on 2013-07-09
Does anybody know if there is a method for finding info on a package before doing sudo apt-get install on terminal?
Thanks

---

### Post by llamabr on 2013-07-09
depends on what you want to know:

[http://newbiedoc.sourceforge.net/tutorials/apt-get-intro/info.html](http://newbiedoc.sourceforge.net/tutorials/apt-get-intro/info.html)

---

### Post by bejiitas_wrath on 2013-07-09
There is some information on mamaging packages with dpkg here: [http://www.securitronlinux.com/bejiitaswrath/useful-bash-commands-and-how-to-manage-packages-with-dpkg-on-a-debian-distro/](http://www.securitronlinux.com/bejiitaswrath/useful-bash-commands-and-how-to-manage-packages-with-dpkg-on-a-debian-distro/) This will give you the information you require. if you have any more questions feel free to ask.

---

### Post by deadflowr on 2013-07-09
```
apt-cache show packagename
```

You can look over the various apt manpages.
man apt-get, man apt-cache.

---

### Post by silv3rm00n on 2013-07-10
```

apt-cache show packagename

or

aptitude show packagename

```

Read a complete [apt tutorial](http://www.binarytides.com/apt-get-tutorial-package-management-ubuntu-commandline/)

---

### Post by oldos2er on 2013-07-10
**dpkg-query**, see ```
man dpkg
```

---

