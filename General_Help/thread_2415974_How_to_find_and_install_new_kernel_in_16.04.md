---
title: "How to find and install new kernel in 16.04"
date: 2019-04-03
forum: General Help
---

### Post by Richard-S on 2019-04-03
I removed kernel 4.4.0.143 from my machine due to the conflict with Virtual Box.

Now my machine does not automatically update to the latest kernel with automatic updates. I am still running 4.4.0.142, whereas yesterday my wife's machine updated to 4.4.0.145.

I cannot find 4.4.0.145 (or any of the 4.4.0.xxx kernels for that matter) on the list of Ubuntu kernels at  [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/) nor does UKUU list it as available. UKUU only lists 4.4.0.141 and 4.4.0.142, which I have installed.

How do I download and install kernel 4.4.0.145?  
AND
How do I get my machine to begin updating the kernel again?

Richard

---

### Post by Impavidus on 2019-04-03
My guess: removing the 4.4.0-143 kernel also removed the meta-packages that pull in new kernels. Reinstall the metapackages and kernel 4.4.0-145 should be installed automatically. It should be```
sudo apt install linux-generic
```but I can't check at the moment because of a server error. If it doesn't work, show the output of```
dpkg --list | grep linux-
```

---

### Post by deadflowr on 2019-04-03
Install linux-generic
That will install the linux-image and linux-headers generic meta packages, which always rely on the latest kernel version Ubuntu offers.
4.4.0-145 is the current version for the 4.4 kernels on Ubuntu.


^ninja'd.
slowly, since I sat here for 10 minutes before clicking on post quick reply.

---

### Post by Richard-S on 2019-04-03
Yes, that worked. Thank you.

Richard

---

