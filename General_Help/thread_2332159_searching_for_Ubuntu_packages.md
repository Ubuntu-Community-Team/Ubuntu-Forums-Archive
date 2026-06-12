---
title: "searching for Ubuntu packages"
date: 2016-07-28
forum: General Help
---

### Post by Skaperen on 2016-07-28
when i run "Ubuntu Software" and do a search, is this (supposed to be) a thorough search across all packages as of the last update (i did yesterday)?  i did a search for "qemu" and it results in "No Application Found" even though i know many packages with "qemu" in the name, exist.  what/where is a better search?

---

### Post by CantankRus on 2016-07-29
Install and use synaptic for your package management.

---

### Post by sudodus on 2016-07-29
I suggest that you install and use synaptic

```
sudo apt-get install synaptic
```

(I tested now. it finds qemu.)

You can also use apt-cache

```
apt-cache policy qemu
```

or even ```
apt-cache policy qemu*
``` but it gives me a rather messy output, so I prefer synaptic for this kind of search.

---

### Post by uRock on 2016-07-29
+1 to install Synaptic. It is better for searching when searching for particular package names. I also recommend running the following commands to allow you to search without having to open the search box. This allows you to add letters or numbers to get the results you are looking for without having to search over and over again.
```
sudo apt-get install apt-xapian-index
sudo update-apt-xapian-index -vf
```

---

### Post by Skaperen on 2016-08-12
to get a list of packages, i did:
```
apt-cache dump|egrep '^Package: '|cut -c 10-
```

---

