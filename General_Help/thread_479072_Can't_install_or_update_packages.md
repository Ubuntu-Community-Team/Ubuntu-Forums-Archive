---
title: "Can't install or update packages"
date: 2007-06-19
forum: General Help
---

### Post by roil13 on 2007-06-19
I've tried updating, using the update manager and it failed. i then tried to update manually using "apt-get update" and got this error message:
```
dpkg: conflicting diversions involving `/ .' or `/ This module can be found as the module 'app/xmodmap' at'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
i can't install anything new, or update. what can i do to fix it?

---

### Post by Beefeater on 2007-06-20
Try

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bakup
sudo apt-get update

---

### Post by roil13 on 2007-06-20
> **Beefeater said:**
> Try

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bakup
sudo apt-get update

i got this error:
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

---

### Post by Ozeuss on 2007-06-20
do you have a status file at all?
what does "ls" show in /var/lib/dpkg"?

---

### Post by roil13 on 2007-06-20
> **Ozeuss said:**
> do you have a status file at all?
what does "ls" show in /var/lib/dpkg"?
i had one until i renamed it.
now ls of /var/lib/dpkg shows:
[COLOR="Blue"]alternatives[/COLOR]  available-old  diversions  lock     [COLOR="Blue"]parts[/COLOR]         statoverride-old  status.bakup  [COLOR="Blue"]updates[/COLOR]
available     cmethopt       [COLOR="Blue"]info[/COLOR]        [COLOR="Blue"]methods[/COLOR]  statoverride  status.bak        status-old

---

### Post by Ozeuss on 2007-06-20
AFAIK, ubuntu has to have a status file. so create a blank one, and then you might try to update.
you might need to remove the lock file in this directory (or rename it), and then update.

If these method don't work, to restore your old status
in /var/lib/dpkg
```
cp status-old status
sudo apt-get update
```
i'm not sure this will solve your problem (but it will restore the older status)
you might want to open the 'diversions' file and check for lines that override each other (very possibly one containing xmodmap) and maybe change the location or something if possible.

---

### Post by roil13 on 2007-06-22
> **Ozeuss said:**
> AFAIK, ubuntu has to have a status file. so create a blank one, and then you might try to update.
you might need to remove the lock file in this directory (or rename it), and then update.

If these method don't work, to restore your old status
in /var/lib/dpkg
```
cp status-old status
sudo apt-get update
```
i'm not sure this will solve your problem (but it will restore the older status)
you might want to open the 'diversions' file and check for lines that override each other (very possibly one containing xmodmap) and maybe change the location or something if possible.

after comparing to someone's else diversions file, it seems like a completely different file. i've compared the other file with  another computer (we have 3 linux boxes at home) i've decided to overwrite my file with one of them. it worked, and so far it seems ok.

thanks to all who tried to help, and for Ozeuss for the tip to compare.

---

