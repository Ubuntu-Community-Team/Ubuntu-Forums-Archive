---
title: "Low volume, distortion after kernel update"
date: 2015-09-04
forum: General Help
---

### Post by broadcast23 on 2015-09-04
This morning I went into my xubuntu install 14.04 LTS to do updates, a new kernel was upgraded.  Then I went to play youtube videos and the volume was low and very distorted.  I rebooted into the previous kernel just now to see if it was the kernel, it was.  It plays fine in kernel 3.13.0-62, but 3.13.0-63 it does not.  All installed are 64 bit

---

### Post by pqwoerituytrueiwoq on 2015-09-04
based on that kernel you are running 14.04
just remove the 3.13.0-62
sudo apt-get purge linux-*3.13.0-62*
you can try the newer 3.19 kernel
sudo apt-get install --install-recommends linux-generic-lts-vivid

---

### Post by broadcast23 on 2015-09-04
OK got it sorted thanks.  Just a note if you virtual box installed, it throws errors, but I uninstalled virtual box and everything is better thanks again.

---

