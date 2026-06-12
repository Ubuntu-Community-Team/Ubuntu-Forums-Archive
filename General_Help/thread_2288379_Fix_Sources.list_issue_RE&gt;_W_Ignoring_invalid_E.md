---
title: "Fix Sources.list issue RE:&gt; W: Ignoring invalid E: Could not open file"
date: 2015-07-26
forum: General Help
---

### Post by whereismymindat2 on 2015-07-26
Thanks for reading. I continue to get errors with what is a "Clean" Sources.list (aka--I can do an apt-get update---all goes well, can install from it..but still get the following remnant errors....

```

E: Could not open file /var/lib/apt/lists/deb.opera.com_opera-stable_dists_stable_non-free_binary-i386_Packages - open (2: No such file or directory)

W: Ignoring file 'opera.list sudo sh -c echo' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```




I have manually cleaned out the few "dupes" I saw in Sources.list. However, how can I "clean"/"flush the 
Data links here ------>  /var/lib/apt/lists/
Data links here ------>/etc/apt/sources.list.d/

Without having to go rebuild over the sources.list file

I have "dozens" (like dozens of dozens of the errors)---thus why I prefer a "flush" solution. Thanks!. 
Thanks!
```

EX: (this will show up 20-30-times in the error log). 
W: Duplicate sources.list entry http://www.gtlib.gatech.edu/pub/ubuntu/ trusty/main i386 Packages (/var/lib/apt/lists/www.gtlib.gatech.edu_pub_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://www.gtlib.gatech.edu/pub/ubuntu/ trusty/main i386 Packages (/var/lib/apt/lists/www.gtlib.gatech.edu_pub_ubuntu_dists_trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://www.gtlib.gatech.edu/pub/ubuntu/ trusty/restricted i386 Packages (/var/lib/apt/lists/www.gtlib.gatech.edu_pub_ubuntu_dists_trusty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://www.gtlib.gatech.edu/pub/ubuntu/ trusty/universe i386 Packages (/var/lib/apt/lists/www.gtlib.gatech.edu_pub_ubuntu_dists_trusty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://www.gtlib.gatech.edu/pub/ubuntu/ trusty/multiverse i386 Packages (/var/lib/apt/lists/www.gtlib.gatech.edu_pub_ubuntu_dists_trusty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://www.gtlib.gatech.edu/pub/ubuntu/ trusty-updates/multiverse i386 Packages (/var/lib/apt/lists/www.gtlib.gatech.edu_pub_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages)

```

---

### Post by CantankRus on 2015-07-26
Isn't that saying you have a file named "**opera.list sudo sh -c echo**" ???
```
ls /etc/apt/sources.list.d | grep opera
```

Command to show all enabled sources...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

