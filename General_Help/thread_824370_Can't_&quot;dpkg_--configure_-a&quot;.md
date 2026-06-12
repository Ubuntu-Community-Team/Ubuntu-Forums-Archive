---
title: "Can't &quot;dpkg --configure -a&quot;"
date: 2008-06-10
forum: General Help
---

### Post by ShareBuntu on 2008-06-10
After installing a custom compiled kernel, and uninstalling it; I can't perform a "dpkg --configure -a" anymore. Here's the output:

```
root@macbook:~# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24.3null
Cannot find /lib/modules/2.6.24.3null
update-initramfs: failed for /boot/initrd.img-2.6.24.3null
dpkg: subprocess post-installation script returned error exit status 1
```
It looks like it's searching for the old kernel, but I'm positive I removed all traces. Any ideas?

---

### Post by iaculallad on 2008-06-10
Try installing util-linux

```
sudo apt-get install util-linux

```

---

### Post by cdtech on 2008-06-10
Try using your synaptic package manager under status > not installed (residual config) and clean those out or do a sudo apt-get autoremove and see if that helps.......

---

### Post by ShareBuntu on 2008-06-10
Thank you for the response. I can't access Synaptic:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Or install anything for that matter:

```
null@macbook:~$ sudo apt-get install util-linux
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

---

### Post by ShareBuntu on 2008-06-10
Managed to fix the problem by removing the custom kernel from /var/lib/initramfs-tools. It still had an entry listed there, not sure if it's a bug or not.

---

