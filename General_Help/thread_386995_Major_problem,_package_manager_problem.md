---
title: "Major problem, package manager problem"
date: 2007-03-17
forum: General Help
---

### Post by malfist on 2007-03-17
When I try to use apt-get (or load package manager) I get these errors:
```

E: Dynamic MMap ran out of room
E: Error occurred while processing ratmenu (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```
I just installed Automatix2 and it installed checkgmail, which doesn't work...
Any ideas how to fix this?

Malfist

Edit: aptitude does the same thing.

---

### Post by strabes on 2007-03-17
Don't know how to fix your problem, except to say that automatix is known to break things.

---

### Post by jackrobinson on 2007-03-17
> **strabes said:**
> Don't know how to fix your problem, except to say that automatix is known to break things.
Automatix fixes things which Ubuntu breaks. Get the facts right.
To the OP:
do the following:
open up /etc/apt/.apt.conf
```
sudo gedit /etc/apt/apt.conf
```

and add the following line in the file that opens up:

> APT::Cache-Limit 2000000;

Save the file and close it and then do a
```
sudo apt-get update
```

to see if that fixes the problem.

---

### Post by malfist on 2007-03-17
sudo mousepad /etc/apt/apt.conf showed an empty file. I had to install backports for something so I have > 600MB to download for updates :(, I'll let you know when I get finished.

---

### Post by jackrobinson on 2007-03-17
> **malfist said:**
> sudo mousepad /etc/apt/apt.conf showed an empty file. I had to install backports for something so I have > 600MB to download for updates :(, I'll let you know when I get finished.

yeah its normal for the file to be empty.

---

### Post by malfist on 2007-03-17
Same errors. apt-get update throws them still after loading a bunch of what looks to be backport stuff.

---

### Post by malfist on 2007-03-17
For some reason I have both Edgy and Dapper repositories enabled, I disabled backports.

---

### Post by malfist on 2007-03-17
Seems to be working now that backports are disabled.

---

### Post by malfist on 2007-03-17
Still getting errors, running sudo apt-get -f install

---

### Post by malfist on 2007-03-17
Works but perl is throwing a lot of warnings...

---

