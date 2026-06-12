---
title: "Uninstalling Software + Dependencies"
date: 2007-01-09
forum: General Help
---

### Post by JPMaximilian on 2007-01-09
I installed "drip" from synaptic, and it had a lot of dependencies, which were downloaded and installed as well.  However, after unsuccesfully using drip, I decided to remove it.  When I removed it, it only removes drip and not the dependencies though, so, now I guess I have a lot of dependencies that I don't need that I don't know how to get off in any practical way.  Is this just how it works, is there a way for me to uninstall them as well?  Thanks.

---

### Post by hashimoto on 2007-01-09
With Synaptic, basically yes. You can however, look at the history data (File > History, if memory serves) to see what all has been installed at the same time to remove the dependencies.

If you are willing to use terminal, you could use Aptitude to install and uninstall programs. Aptitude can automatically remove dependencies.

---

### Post by JPMaximilian on 2007-01-09
what would the commands be if i used apt?

---

### Post by tarun86 on 2007-01-09
Use 
$apt-get autoremove 
This will remove all the unwanted packages that are installed!! so if the dependencies installed with drip are used somewhere it wont be removed else it will be !!

---

### Post by JPMaximilian on 2007-01-09
Excellent, thanks!

---

