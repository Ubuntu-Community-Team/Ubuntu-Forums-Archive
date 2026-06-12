---
title: "Determining under which user a process is running (apache2)"
date: 2007-11-18
forum: General Help
---

### Post by winhamwr on 2007-11-18
Hello,

I'm working through my first Ubuntu installation to use as a LAMP development machine. I'm trying to debug some problems with my apache2 process and permissions. I installed apache2 through apt-get and it was running successfully with the default start page. I've changed the documentRoot to another directory and now I'm getting permission problems with apache when I load localhost in the browser. So my question is:

-How do I use ps (or whatever tool) to determine under which user the apache2 process is running? I've read through the man page and tried using ps -e -M which I thought would give me security information, but it didn't give me the user the process was running as.

-I have a suspicion that apache2 is running as root. Does anyone know of a good guide I can use to set the apache2 process as some other user (like www-data, which is how I've seen apache configured on systems which my noob self didn't install/configure). I have that suspicion because when I run users-admin, there is no www or www-data users or groups.

Any help or pointers to relevant guides would be much appreciated. I've found tons of apache setup guides, but I'm having a more difficult time finding guides on how to start a process as a particular user, or determine which user a process is running under. 

thanks.

---

### Post by jamvegan on 2007-11-18
```
ps aux
```

(Note that there is no -, since these are BSD-style options.)

---

### Post by winhamwr on 2007-11-18
Perfect. Thanks a ton.

The main apache process is running as root but all of the spawned processes are running as www-data, so everything is looking good.

---

