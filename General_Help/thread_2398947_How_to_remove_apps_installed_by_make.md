---
title: "How to remove apps installed by make"
date: 2018-08-20
forum: General Help
---

### Post by neovich on 2018-08-20
I installed varnish using this commands
```

cd /tmp && git clone https://github.com/varnishcache/varnish-cache
cd varnish-cache
sudo sh autogen.sh
sudo sh configure
sudo make

```

and now want to remove it. It placed in the 
```

neo@neo:/tmp/varnish-cache$ which varnishd/usr/local/sbin/varnishd

```

How to remove it? 
**sudo apt-get remove** doesn't help

---

### Post by TheFu on 2018-08-20
You need read the INSTALL file and README files for instructions.  Things installed into /usr/local/ are 99.99999% manually installed and not tied into the package manager. That almost always means you can just delete files and the settings in /usr/local/etc/ for removal.

But read the documentation provided.

---

