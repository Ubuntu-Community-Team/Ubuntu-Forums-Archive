---
title: "proper way of cleaning up partitions"
date: 2008-06-04
forum: General Help
---

### Post by akahige on 2008-06-04
My boot partition has been slowly filling up over the various upgrades and is now in need of being cleaned up/thinned out. What's the best/appropriate way of doing this?


Along those lines, I ran into an issue awhile back that got answered on the IRC channel and I can't seem to find the reference note I made... my var partition filled up with what was apparently cached packages. What directory(s) they go in so that I can periodically clean them out...?

---

### Post by fragos on 2008-06-04
Open Synaptic and do a search on your linus OS version, 2.6.24 for Ubuntu 8.04. The results will all the the various kernel packages. You'll notice that 2.6.24 has an extension as in 2.6.24-18. Mark for removal packages older than -18 with extensions like -17 and -16. This will clean them out and also update grub.

---

### Post by akahige on 2008-06-04
I'm looking here at the list in Synaptic, but when I check a package, the only thing it will allow me to do is mark it for installation. The "mark for removal" option is greyed out, even though I had to use the admin p/w to get Synaptic to open.

What am I missing?

---

### Post by akahige on 2008-06-04
Apparently, what I was missing was the fact that Synaptic gave me everything, and I didn't scroll far enough to see the check marks for the things that I had installed.

Okay... having gone through the recommended uninstall process, it gave me a rather nonspecific error about not being able to uninstall one of the -16 packages. Should I be worried about this? Is it going to cause me problems?

And in looking at the /boot, I see that there are even older kernel files that need to be purged.

---

### Post by akahige on 2008-06-04
Removing older kernel packages in Synaptic, I got error. In doing "sudo apt-get upgrade", I got more info:

```
#
(Reading database ... 116541 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Something seems to be stuck. The files it's looking for are gone -- removed by the Synaptic uninstall, I guess. All except this modules package that won't go away. What's the proper way of getting rid of this thing?

---

### Post by fragos on 2008-06-04
The older version package won't be accessed unless you boot to that version. Kernels prior to your current distro can be deleted with sudo and rm. You may also need to edit /boot/grub/menu.lst so they aren't offered for boot any more.

---

### Post by VMC on 2008-06-04
> **akahige said:**
> Removing older kernel packages in Synaptic, I got error. In doing "sudo apt-get upgrade", I got more info:

```
#
(Reading database ... 116541 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Something seems to be stuck. The files it's looking for are gone -- removed by the Synaptic uninstall, I guess. All except this modules package that won't go away. What's the proper way of getting rid of this thing?

Look into "apt-get <option>  --purge".

---

### Post by akahige on 2008-06-04
I understand that. And I think everything is gone except for the db link(s).

Is there no way to get this orphan out of the database so it doesn't kick errors every time I apt-get upgrade?

---

### Post by Ragnar Bocephus on 2008-06-05
Any word of this at all?  I'm having the same problem.  :confused:

---

### Post by akahige on 2008-06-05
The solution wound up being to reinstall the problem package and then to do "remove all". Seemed to work just fine.

---

### Post by Ragnar Bocephus on 2008-06-05
^Thanks for that.  It took a few tries, but I was finally able to get rid of the thing and get my upgrades.  Everything's working great again now.

---

### Post by akahige on 2008-06-05
Glad it worked for you.

---

