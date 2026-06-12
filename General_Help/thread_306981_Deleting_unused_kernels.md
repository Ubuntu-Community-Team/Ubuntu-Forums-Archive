---
title: "Deleting unused kernels"
date: 2006-11-25
forum: General Help
---

### Post by Athanasius on 2006-11-25
There are kernels on my GRUB list that I do not use including one that I installed that I did not know was obsoleted by the present generic kernel included in edgy.  Where do I look for the kernels and is it safe to delete them?  Are there other files that should be deleted with the kernels?

---

### Post by fritz_monroe on 2006-11-25
I've removed all but the past 2 kernels.  I used Synaptic.  In Synaptic, you just select the kernels that you don't want on the list and it deletes them along with the other files.  I don't recall if I had to manually remove the lines from Grub or not, but if you find they need manually removed, just use a text editor to remove the lines.

---

### Post by moshuptrail on 2006-11-25
I started to try this using synaptic, but when came to the confirmation I noticed that each kernel frees up less than 100Mb.  On a machine with Gb's to spare a few hundred Mb's is not much.  Not worth the risk.  Perhaps the best choice is to simply remove the entries from Grub.

---

### Post by Athanasius on 2006-11-25
I'll try that, thanks

---

### Post by tomcheng76 on 2006-11-26
just type
sudo apt-get remove linux-image-<your old kernel ver>
where <your old kernel ver> is something like 2.6.17-10-386 , this is the latest 386 kernel, haha
then your menu.lst will be automatically updated too, no risk

---

