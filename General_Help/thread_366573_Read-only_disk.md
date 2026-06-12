---
title: "Read-only disk??"
date: 2007-02-21
forum: General Help
---

### Post by icehammer on 2007-02-21
Since yesterday, i'm triple-booting XP, Vista and Ubuntu... However, while the dualboot of XP-ubuntu used to work fine, with this new config (pl note that i fprmatted all my drives, then installed xp first, then vista and finally ubuntu), all my drives in ubuntu are rendered as "Read-only" drives.. I can't even rename a single anywhere on any of my drives...

What should i do??

---

### Post by Spr0k3t on 2007-02-21
Try doing this:

```
sudo mount -a -o rw
```

You may get an error message stating the file system needs to be checked.  I've found that sometimes when this happens, you still get the drive to mount and it's read/write capable.  Keep in mind that you will need to make sure the drives are not compressed, otherwise you will have read only capabilities.

---

### Post by Viper666 on 2007-02-21
use ntfs-3g and this will give u full read/write access on the partitions

---

### Post by icehammer on 2007-02-21
I tried ntfs-3g, but when i do 

```
sudo apt-get install ntfs-config
```

i get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages
```


what to do now??
i tried installing libdbus-103 and 1-2 manually..
but it still says the same thing..

---

### Post by givré on 2007-02-21
> **icehammer said:**
> 
i tried installing libdbus-103 and 1-2 manually..

You should not do that kind of thing, that could be dangerous.
Where did you get ntfs-config (which repo) ?

---

### Post by kingdave9 on 2007-03-03
I get the exact same error message when I try to run ntfs config:

The following packages have unmet dependencies:
  ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages

:(

---

### Post by Mangiafuoco on 2007-03-13
me too but in italian...

```
I seguenti pacchetti hanno dipendenze non soddisfatte:
  ntfs-config: Dipende: libdbus-1-2 (>= 0.60) ma non è installabile
E: Pacchetto non integro
```

how to resolve?

---

### Post by Mangiafuoco on 2007-03-13
I resolved.
I dowloaded the packets for dapper but I've got edgy...

---

