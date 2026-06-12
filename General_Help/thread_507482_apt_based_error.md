---
title: "apt based error?"
date: 2007-07-23
forum: General Help
---

### Post by mymyheyhey on 2007-07-23
Whenever I try to install something it will go through the processes but not actually do it. When i watch what its doing in the terminal I get this error:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 6755 package `gnome-nettool': 
 `Depends' field, invalid package name `libgtk2*0-0': character `*' not allowed (only letters, digits and characters `-+._') 
E: Sub-process /usr/bin/dpkg returned an error code (2) 

Im using Fiesty, but this only showed up after I installed automatix.

Many Thanks,

---

### Post by tbroderick on 2007-07-23
Try entering;

```

sudo dpkg --clear-avail
```

Then
```

sudo apt-get update
```

---

### Post by mymyheyhey on 2007-07-23
ok, done them, the sudo apt-get update command goes through and gets stuck on:

99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.9)]                       

but I assume thats automatix's website fault.


So just being me, what did those commands actually do?

---

### Post by tbroderick on 2007-07-23
> **mymyheyhey said:**
> ok, done them, the sudo apt-get update command goes through and gets stuck on:

99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.9)]                       

but I assume thats automatix's website fault.


So just being me, what did those commands actually do?


Something messed up dpkg, maybe automatix. Basically, you just cleared the list of available packages. Nothing major. You can take a look at 'man dpkg' for further reference.

---

