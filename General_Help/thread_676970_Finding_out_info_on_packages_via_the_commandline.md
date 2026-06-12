---
title: "Finding out info on packages via the commandline"
date: 2008-01-24
forum: General Help
---

### Post by nibirumarduk on 2008-01-24
Hello. Can someone tell me how I can go about finding out the total number of packages I have installed in my system via the commandline?

Also how can one know the total number of packages there is for a release such as gutsy and for e.g. main, restricted, universe, multiverse, gutsy-updates, gutsy-security from the commandline? I remember seeing some commands that involves grep on the /var/apt or the /var/lib/dpkg directories I think. Anyone?

---

### Post by archivator on 2008-01-24
To count all the installed packages, I do a ```
aptitude search ~i | grep -c i
```. This makes aptitude list all the installed packages and grep then counts all the lines which have *i* in them. That is, it counts all the lines.

As for the repos, I can't really help you there.

---

### Post by y-lee on 2008-01-24
> **nibirumarduk said:**
> Hello. Can someone tell me how I can go about finding out the total number of packages I have installed in my system via the commandline?

Try **apt-cache stats**

I don't know the answer to the second question.

Also of interest tho is


```
dpkg --get-selections | grep -v deinstall | sed -e 's/[    ]install//g' | sed -e 's/    //g' >install.txt
```

which saves all installed software to a a text file. :)

---

### Post by y-lee on 2008-01-24
Duh I was mistaken

apt-cache stats Gets statistics about the packages available in the repositories  so it answers your second question. And archivator answered your first. 

I'm a Noob here. lol

---

### Post by nibirumarduk on 2008-01-24
Thank you both archivator  and y-lee. Much appreciated. :popcorn:

---

