---
title: "microcode update - HELP!"
date: 2018-08-16
forum: General Help
---

### Post by hmiersch on 2018-08-16
hi. for the last few weeks the software updater keeps bringing up a microcode update for AMD CPUs which is useless to me because i have an intel CPU. some time after that AMD update appeared, an intel equivalent appeared which i installed. so why does it keep bringing up that AMD update? how can i get rid of the frigging thing? i don't want to install it, not even accidentally, because that would probably brick my new computer. so what can i do?

---

### Post by deadflowr on 2018-08-16
microcode updates are now dependencies of the kernel:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259")

but more then that, installing the amd microcode on intel will not do anything.
It would be like installing an update for chromium and thinking it would affect firefox.

---

### Post by QIII on 2018-08-16
To add to that ...

Kernels have hundreds or even thousands of modules compiled in.  The ones not needed are simply not loaded by the kernel on startup if they are not applicable.  That's how the same kernel can be used on all manner of hardware configurations without having to be specifically targeted.  If it were not that way, specific kernels would have to be produced and compiled for a million different possible configurations.

Cheers!

---

### Post by Yellow Pasque on 2018-08-16
Update it and get on with life.
Or...
If it really bothers you, try removing the package.
```
sudo apt-get purge amd64-microcode
```
Just make sure no other packages are removed before you confirm the decision. Here on Debian, you can remove the amd or intel microcode packages without removing anything else, but I can't guarantee that Ubuntu has the dependencies laid out exactly the same way.

---

### Post by hmiersch on 2018-08-17
```
sudo apt-get purge amd64-microcode
```  that did the trick. thanks.

---

### Post by mörgæs on 2018-08-17
Good, please mark the thread solved.

---

### Post by hmiersch on 2018-08-17
> **mörgæs said:**
> Good, please mark the thread solved.  how do i do that?

---

### Post by ajgreeny on 2018-08-17
Please mark as SOLVED from the Thread Tools menu up-top of this thread, if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by hmiersch on 2018-08-17
Found it :-)

---

