---
title: "Glibc missing in Hoary ?"
date: 2005-04-14
forum: General Help
---

### Post by frederictoulouse on 2005-04-14
Hi !

I tried to install softwares like MySQL Query Browser or to compile sylpheed in Hoary and I have always an error because Glibc is missing in Hoary :

./bin/mysql-query-browser
./bin/mysql-query-browser-bin: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by ./bin/mysql-query-browser-bin)


How can I solve this problem ? many software needs glibc...

thanks

---

### Post by XDevHald on 2005-04-14
To get the package installed type as root:


[b]apt-get update

apt-get install libg++2.8.1.3-glibc2.2

apt-get install libstdc++2.10-glibc2.2

apt-get upgrade

[/b]This is the latest version of glibc for breezy, hopefully hoary is the same.

---

### Post by snap monkey on 2005-05-15
I've also had trouble with this.  Tried those commands with Hoary and no luck, said that it couldn't find those .  Anyone know which packages to get for Hoary?

---

