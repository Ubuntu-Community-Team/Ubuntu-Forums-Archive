---
title: "Cannot update packages"
date: 2007-06-28
forum: General Help
---

### Post by Norm2787 on 2007-06-28
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 7196 package `avahi-autoipd':
 newline in field name `G'
E: Sub-process /usr/bin/dpkg returned an error code (2)

I am new to Ubuntu 7.04 and really don't know my way around. It says I have 459 broken dependencies?

---

### Post by eggdeng on 2007-06-28
Try ```
sudo apt-get update
``` followed by ```
sudo apt-get upgrade
```

---

### Post by Norm2787 on 2007-06-28
Tried sudo apt-get upgrade -f still have this error 
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 7196 package `avahi-autoipd':
 newline in field name `G'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by eggdeng on 2007-06-28
Seems that the database file which holds data about the status of packages on your system is corrupt. If you do a ```
ls  /var/lib/dpkg
``` you'll see a backup file called ```
status-old
``` So you could try backing up the current ststus file and replacing it with this. If that fails, this is a link to a script which is supposed to generate a new status file [file.http://tuxx-home.at/projects/restore-dpkg-status.sh.html]("file.http://tuxx-home.at/projects/restore-dpkg-status.sh.html") Else just google /var/lib/dpkg/status for more options.

---

