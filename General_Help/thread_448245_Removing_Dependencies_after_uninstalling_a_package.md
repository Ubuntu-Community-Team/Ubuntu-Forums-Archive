---
title: "Removing Dependencies after uninstalling a package?"
date: 2007-05-18
forum: General Help
---

### Post by true_friend on 2007-05-18
Hi folks
I am in a confusion how to remove the dpendencies of a package which i have uninstalled. (i did not removed the dependencies when i removed it from synaptic). It was about 40 MB when I downloaded and installed it but now only 600 KB is removed it mean dependencies are still there occupieng space. 
Any ideas?
Regards
True_Friend

---

### Post by TriggerHappyChewie on 2007-05-18
sudo apt-get autoremove

You also might want to clear out the downloaded *.deb's in /var/cache/apt/archives

---

### Post by wdaniels on 2007-05-18
> **TriggerHappyChewie said:**
> sudo apt-get autoremove

You also might want to clear out the downloaded *.deb's in /var/cache/apt/archives

"sudo apt-get clean" for the latter.

---

### Post by true_friend on 2007-05-19
thnx it worked fine.

---

