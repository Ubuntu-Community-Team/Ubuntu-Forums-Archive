---
title: "Accidentally Deleted Kernel"
date: 2013-12-17
forum: General Help
---

### Post by Tristan_Williams on 2013-12-17
Hello everyone, I would like to share a little bit of knowledge.

About 10 minutes ago I deleted my kernel accidentally, which made me unable to boot the system.

To fix this, I booted my handy dandy LiveUSB and opened my terminal. 

The fix is simple really. All I had to do was type the following commands:
```

sudo apt-get -o Dir=/media/[location of main drive] install [package name of kernel]

```

so in my case it was:
```

sudo apt-get -o Dir=/media/tristan401/[a bunch of letters and numbers] install linux-image-lowlatency

```


After that is installed, just type the following:
```

cd /media/[location of main drive]
sudo update-grub && sudo update-grub2

```


I hope this information helps someone :)

---

