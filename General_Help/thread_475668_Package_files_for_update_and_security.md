---
title: "Package files for update and security"
date: 2007-06-16
forum: General Help
---

### Post by ronbrooks on 2007-06-16
I have just reinstalled Ubuntu 7.04 again and am now on about 20+ hours of updates and security update files as I am on dial up network.  I still have not started to down load programs that I need yet. 

My question is I have another computer that I want to install Ubuntu on but I don't want to go through the long down load of the updates and security files.  When you down load the files before they get installed on the system where are they stored and can they be copied to a cd and then mover to the second computer and put them back in the same place.  Then run update and have them installed in the other computer.  That way I don't have to spend hours down loading the same files again.

Can someone tell me if it can be done and how to do it. It would save me a lot of time

Thanks for your help.

---

### Post by _duncan_ on 2007-06-16
> ,,,When you down load the files before they get installed on the system where are they stored,,,

/var/cache/apt/archives

Copy the contents into the same folder on another installation. Go through the process of updating the system. The update manager will *see* these files and no longer download from the ubuntu repository.

Also works great for reinstalls on the same computer.

---

### Post by ronbrooks on 2007-06-18
Thanks a lot that is just what I was looking for.

---

