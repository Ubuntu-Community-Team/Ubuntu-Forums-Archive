---
title: "What's the difference between Ubuntu OS and ubuntu-desktop packet"
date: 2017-01-18
forum: General Help
---

### Post by bsun003 on 2017-01-18
Hi all,

I recently met the similar problem as the following link when I was trying to fix no sound problem. The solution of reinstalling ubuntu-desktop helped me solve my problem. My question is: what is the packet of ubuntu-desktop. Is it the desktop version of OS or the desktop application of Ubuntu? In other words, after running the command "sudo apt-get install ubuntu-desktop", will it reinstall the whole Ubuntu OS or the desktop application? It seems to be the desktop application because the software that I installed before didn't be erased. 

[http://askubuntu.com/questions/453440/missing-system-settings-after-removing-some-packages](http://askubuntu.com/questions/453440/missing-system-settings-after-removing-some-packages)

Thanks and regards,

Bojun

---

### Post by ajgreeny on 2017-01-18
Ubuntu OS, as you call it, is the full installation of the operating system.
Ubuntu-desktop package is simply a metapackage; it is not an application as such, but merely a package with a list of dependencies, and those dependencies are the full list of packages in the normal installation of Ubuntu OS.

Therefore, if you remove a package from your full installation and it takes with it several other packages that are needed for the full OS to work as normal, you can usually get back to the original by installing ubuntu-desktop. That will normally bring with it the packages you have removed to get back to a complete Ubuntu OS.

---

### Post by bsun003 on 2017-01-18
Thanks for the reply. This is much clear to me. Therefore, the ubuntu-desktop can be seen as a recovery or backup packet right?

---

### Post by ajgreeny on 2017-01-18
I suppose so, but that is not its real intention.

---

### Post by ian-weisser on 2017-01-19
> **bsun003 said:**
> The ubuntu-desktop can be seen as a recovery or backup packet right?
Only in the limited sense that it will reinstall other removed packages. It will have no effect upon packages that are still installed but misconfigured or broken.

---

