---
title: "Autoremove wants to remove gstreamer0.10"
date: 2017-05-14
forum: General Help
---

### Post by Ralph L on 2017-05-14
I am trying to clean up my computer and ran 
sudo apt-get autoremove.
It responded with ```
The following packages will be REMOVED:
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libzip4 linux-headers-4.4.0-64 linux-headers-4.4.0-64-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-64-generic snap-confine

```  Is it ok to remove gstreamer0.10??  I see that gstreamer1.0 is installed.  Is this enough??

---

### Post by vasa1 on 2017-05-14
Your distro is listed as```
Xubuntu 14.04 Trusty Tahr
```in your profile. Is that correct? If not, please edit your profile or provide the correct information here.

---

### Post by Dennis N on 2017-05-14
autoremove has determined you have no software that depends on gstreamer0.10 packages, so it's ok to remove them.

---

### Post by kostkon on 2017-05-14
Most software now uses the 1.x branch, so yeah it's safe to remove.

---

### Post by Ralph L on 2017-05-17
Thanks for the responses.  I appreciate it. A couple of item:
1.  I am running Xubuntu 16.04 with Kernel 4.8.0-51-generic (according to uname -r).
2.  I will go ahead and autoremove gstreamer0.10.

Thanks again.

---

### Post by vasa1 on 2017-05-17
> **Ralph L said:**
> Thanks for the responses.  I appreciate it. A couple of item:
1.  I am running Xubuntu 16.04 with Kernel 4.8.0-51-generic (according to uname -r).
...
You can click on "Settings" near the right-hand top corner and update your distro information:

---

