---
title: "Cannot install anything with apt-get install"
date: 2018-01-16
forum: General Help
---

### Post by sys320 on 2018-01-16
Hi,

I've just started learning Ubuntu, but I'm stuck at the very beginning. I tried to install 7-zip with the help of this video

[video=youtube;F3l3moI5M6w]https://www.youtube.com/watch?v=F3l3moI5M6w[/video]

Instead of what can be seen in the video I get this:

[IMG]https://abload.de/img/aptpvrey.jpg[/IMG]

It seems like the apt-get install command does not work at all. I get the same result whatever I'd like to install.


This is the most recent verion of ubuntu on a V-box, which is added to the firewall as an exception. I experience no network issues on this instance of Ubuntu, I can access the internet etc..

Any help would be appreciated.

---

### Post by howefield on 2018-01-16
Thread moved to the "*General Help*" forum.

Your error generally means that you have more than one instance of apt running, perhaps the update manager ?

---

### Post by cruzer001 on 2018-01-16
Its telling you that you have another package manager open (maybe the software center).  Only one can be open at a time (apt is also a package manager).

Is there a reason your using the terminal?

---

### Post by DuckHook on 2018-01-16
> **sys320 said:**
> It seems like the apt-get install command does not work at all. I get the same result whatever I'd like to install.
If you are running Artful, I ran into the same problem. Your case may be different, but in my case it was caused by the update manager set to its default setting of "automatically download all updates". This caused an invisible instance of apt to run at every startup. It would not surrender the lock until a few minutes after login. Sometimes, when a large update was pending, the downloads took up to 30 minutes. I solved my problem by turning the update service to "notify only". Now, apt is not locked after login.
> **cruzer001 said:**
> …Is there a reason your using the terminal?
Many people (including yours truly) like installing from the terminal. It gives us much finer-grained control.

---

### Post by cruzer001 on 2018-01-16
Or maybe its an install from the mini.iso (or the server.iso; my choice way) and he may be rolling his own.  There can be other reasons, just wanted to know.

And OP is after that finer-grained control; he's trying to install synaptic :)

---

### Post by Cavsfan on 2018-01-16
> **cruzer001 said:**
> Is there a reason your using the terminal?

> **DuckHook said:**
> If you are running Artful, I ran into the same problem. Your case may be different, but in my case it was caused by the update manager set to its default setting of "automatically download all updates". This caused an invisible instance of apt to run at every startup. It would not surrender the lock until a few minutes after login. Sometimes, when a large update was pending, the downloads took up to 30 minutes. I solved my problem by turning the update service to "notify only". Now, apt is not locked after login.

Many people (including yours truly) like installing from the terminal. It gives us much finer-grained control.

Most of us also purge unattended-upgrades right after installation to prevent messes like this since we only update via terminal.
```
cavsfan@cavsfan-Le-Beast:~$ apt-cache policy unattended-upgrades
unattended-upgrades:
  Installed: (none)
  Candidate: 0.98ubuntu2
  Version table:
     0.98ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
```

This way the only possible way to get this error is while Software Updater is running and visable. One just needs to close that to get rid of that error.

---

### Post by DuckHook on 2018-01-16
> **Cavsfan said:**
> Most of us also purge unattended-upgrades right after installation to prevent messes like this since we only update via terminal…
Excellent suggestion. Still so much to learn after all these years.

---

### Post by Cavsfan on 2018-01-16
> **Cavsfan said:**
> [COLOR=#000000]*Most of us also purge unattended-upgrades right after installation to prevent messes like this since we only update via terminal&#8230;*[/COLOR]

> **DuckHook said:**
> Excellent suggestion. Still so much to learn after all these years.

Everything is always changing... I learned that earlier this year from *howefield* and am glad I did:

[https://ubuntuforums.org/showthread.php?t=2356536&page=2&p=13625357#post13625357](https://ubuntuforums.org/showthread.php?t=2356536&page=2&p=13625357#post13625357)

---

