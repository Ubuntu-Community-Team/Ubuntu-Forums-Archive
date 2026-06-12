---
title: "Synaptic and update manger nothing but blank screens"
date: 2013-08-08
forum: General Help
---

### Post by ed5 on 2013-08-08
I Don't know what happened, but when I try to open either one of them I just get a blank white screen.

Getting this error message from update manager now:

Could not initialize the package information. An unresolvable occurred while initializing the package 
 information. Please report this bug against the "update manager"
E:line 2 too long in source 1 /etc/apt/sources list, E: The list of resources could not be read is the message

I get the same message when trying to open Synaptic package manager.

---

### Post by plucky on 2013-08-08
> **ed5 said:**
> I Don't know what happened, but when I try to open either one of them I just get a blank white screen.

Getting this error message from update manager now:

Could not initialize the package information. An unresolvable occurred while initializing the package 
 information. Please report this bug against the "update manager"
[color=red]E:line 2 too long in source 1 /etc/apt/sources list, E: The list of resources could not be read is the message[/color]

I get the same message when trying to open Synaptic package manager.

Open a terminal and post output for ```
cat /etc/apt/sources.list
```

---

### Post by ed5 on 2013-08-08
> **plucky said:**
> Open a terminal and post output for ```
cat /etc/apt/sources.list
```


deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main #Ubuntu Tweak Stable Source

---

### Post by ed5 on 2013-08-08
This is an interesting one.  I tried the command you sent and it claimed there was no such file. So I went
into /etc/apt/ logged in as administrator and found THREE sources.list files in it...no wonder the computer was
confused.  Two of the file were created the last time I downloaded updates (I checked the dates on them).
The other files was only a couple of week older than them so I switched back to it and the computer works perfectly
again.  Needless to say I made a backup copy of the good sources.list file. Hope this helps some else fix their computer.

---

