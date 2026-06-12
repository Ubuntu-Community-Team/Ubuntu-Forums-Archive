---
title: "[SOLVED] i need help with a dpkg error"
date: 2008-06-09
forum: General Help
---

### Post by afbase on 2008-06-09
well here is my dpkg error.  I type this in and i get this in return:

```

$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script returned error exit status 1

```

I can't use 'apt-get' nor the synaptic package manager because of it.   these two programs suggest doing  a 'sudo dpkg --configure -a' but each time i do it, i run into this problem.

Is there a way to fix this???  By the way, my /boot partition is only 50 megs.  look at my partitions for yourself:

```

clinton@clinton-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8            139644496  11943336 120663488  10% /
varrun                 1687500       108   1687392   1% /var/run
varlock                1687500         0   1687500   0% /var/lock
udev                   1687500        76   1687424   1% /dev
devshm                 1687500        12   1687488   1% /dev/shm
lrm                    1687500     38176   1649324   3% /lib/modules/2.6.24-18-generic/volatile
/dev/sda7                46633     41250      2975  94% /boot
gvfs-fuse-daemon     139644496  11943336 120663488  10% /home/clinton/.gvfs


```


Any suggestions would be appreciated. thanks.

---

### Post by plucky on 2008-06-09
> gzip: stdout: No space left on device
/dev/sda7                46633     41250      2975  94% /boot


You need to either enlarge your /boot partition or clear out some of the files in there.To see what is there ```
ls -l /boot
``` lowercase L not a 1.
You probably have some kernels you don't need anymore,so to clear out use the **Synaptic Package Manager** and search for **Linux-image**.

Probably a good idea to keep a spare kernel.so keep 17 and 18 and remove all the other ones.

Then ```
sudo dpkg --configure -a
``` and away you go.

Good Luck

---

### Post by forgoodorforawesome on 2008-06-11
I'm having the exact same issue, but I can't use the Synaptic Package Manager to fix the problem.  When I start it, it gives me this error:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Is there a way to do this manually?

---

### Post by overdrank on 2008-06-11
> **forgoodorforawesome said:**
> I'm having the exact same issue, but I can't use the Synaptic Package Manager to fix the problem.  When I start it, it gives me this error:



Is there a way to do this manually?

HI and that would be the terminal located under applications, accessories. Then enter that command ```
sudo dpkg --configure -a
```

---

### Post by forgoodorforawesome on 2008-06-11
I tried running dpkg, got the error above, and then when I stumbled up this post I tried to fix the problem using Synaptic package manager.  I can't start up the package manager because of the error I posted above.  When I asked if there was a way to manually do it, I was wondering if it was, in general, "safe" to get rid of the .16 kernels I see in there.  Here is the error I get when running dpkg:

> sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1


---

### Post by plucky on 2008-06-11
```
sudo dpkg purge linux-image-2.6.24-16-generic
```

Should remove that kernel and listing from menu.lst.

Good Luck

---

