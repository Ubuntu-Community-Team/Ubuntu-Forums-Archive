---
title: "How do I list available packages from apt-get or dpkg?"
date: 2008-02-11
forum: General Help
---

### Post by none-letmebe on 2008-02-11
Dear everybody,

I would like to obtain a list of available packages from apt-get or dpkg.
Does anyone know what the options are to do this.

I thought that it was something along the lines of : apt-get list_installed, or dpkg list_installed, but I am wrong.


Any ideas?

---

### Post by kellemes on 2008-02-11
You mean "dpkg -l" maybe?

---

### Post by none-letmebe on 2008-02-11
I thought -l listed the ones that were currently installed.  Am I wrong?

I just did a quick dpkg -l  on a 7.1 install at work on Ubuntu.  I know that privoxy wine and wireshark are not installed and a dpkg -l |grep wireshark , or a grep privoxy or wine does not return these packages.  Thus I think that the -l only lists currently installed packages and not all available packages.

---

### Post by kellemes on 2008-02-11
Not sure if this still works, and can't test it currently..
Try
```
dpkg -l \*
```

Edit: You can always use dselect or aptitude to get a list. [Helpfull link]("http://www.aboutdebian.com/packages.htm")

---

### Post by geirha on 2008-02-11
```

aptitude search '.*'
apt-cache search '.*'
grep -h 'Package: ' /var/lib/apt/lists/* | cut -d' ' -f2 | sort -u

```

These commands at least display a lot of packages, though the ammount of packages they display differs. Not sure why. The first two probably filters out some virtual or deprecated packages ..?

---

### Post by kesman on 2008-02-11
Use synaptic or add/remove to see available packages more easily.

---

### Post by zvacet on 2008-02-11
```
dpkg --update-avail 
```

or 

```
dpkg --merge-avail
```

Read  **man dpkg**

---

