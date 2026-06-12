---
title: "No Sound in Flash"
date: 2005-06-02
forum: General Help
---

### Post by Gunadic on 2005-06-02
I recently installed the flashplayer-mozilla package, but I'm still not getting any sound from any flash files. Help would be greatly aprecciated... this is driving me up the wall  ](*,)  Thanks alot!

---

### Post by Caffeine on 2005-06-02
So I'm not the only person suffering this problem?  I just installed Ubuntu on the weekend, and this has been the first problem I've run across.  I have sound for everything else though without any problems.

---

### Post by m0biu5 on 2005-06-02
[QUOTE=Caffeine]So I'm not the only person suffering this problem?  I just installed Ubuntu on the weekend, and this has been the first problem I've run across.  I have sound for everything else though without any problems.[/QUOTE]
 Yeah, the same happened here. Not sure why there is no sound..

I will be watching this thread :)

---

### Post by Toddy on 2005-06-02
To add sound to flash in Firefox, you need to:

 sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---

### Post by m0biu5 on 2005-06-02
[QUOTE=Toddy]To add sound to flash in Firefox, you need to:

 sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1[/QUOTE]
 Okay, that worked. Being so new to linux, I am not sure **why** that worked...

---

### Post by Gunadic on 2005-06-02
I've tried what you said to do Toddy, yet theres still absolutely no sound coming through my speakers... Hrm...

---

### Post by Caffeine on 2005-06-02
[QUOTE=Toddy]To add sound to flash in Firefox, you need to:

 sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1[/QUOTE]

Tried this out, restarted Firefox, and I now have sound for flash movies.  Excellent.  Has this been a common problem with Firefox on Linux distro's?

---

### Post by Toddy on 2005-06-02
It appears that this been a long standing issue.  I read about this tip here:

[http://www.ubuntulinux.org/wiki/SoundProblemsHoary](http://www.ubuntulinux.org/wiki/SoundProblemsHoary)

---

