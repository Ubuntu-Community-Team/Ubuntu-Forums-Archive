---
title: "Error trying to reinstall nvidia-new drivers Hardy"
date: 2008-06-22
forum: General Help
---

### Post by lukemack on 2008-06-22
E: nvidia-glx-new: subprocess post-removal script returned error exit status 2

Anyone know how to recover from this? I am not able to enable the nvidia drivers so want to reinstall them but I get the above error when I try in Synaptic package manager (same with apt-get).

Version is Hardy 8.0.4 Desktop nVidia 8800 card.


thanks,

lukemack.

---

### Post by bodhi.zazen on 2008-06-22
There is an "old" bug, I do not now if you have the same or not.

```
sudo apt-get remove -purge nvidia-glx-new
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

If that fails, I suggest you search launchpad and if needed file a bug report.

In that event try the nvidia driver.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by lukemack on 2008-06-23
thanks - a reinstall using the -f option of apt-get sorted it.

---

