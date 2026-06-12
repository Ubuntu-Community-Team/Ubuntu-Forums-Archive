---
title: "/usr/src/linux-headers-3.2.0-32-generic/Documentation/devices.txt not there?"
date: 2012-11-04
forum: General Help
---

### Post by Bad.Wulf on 2012-11-04
I was wondering if someone could tell me why devices.txt is not present in my kernel source tree?  /usr/src/linux-headers-3.2.0-32-generic/Documentation. Does this file still exist, is it in some other form?  I'm running ubuntu 12.04.

I've started into learning the basics of module programming using [http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN425](http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN425) as one of my guides and I realize it is a bit dated as the kernel is 2.6.  Does this file still exist, is it in some other form?

Also, as an aside, I'd appreciate direction to any more kernel module programming.

---

### Post by idoitprone on 2012-11-04
> **Bad.Wulf said:**
> I was wondering if someone could tell me why devices.txt is not present in my kernel source tree?  /usr/src/linux-headers-3.2.0-32-generic/Documentation. Does this file still exist, is it in some other form?  I'm running ubuntu 12.04.

I've started into learning the basics of module programming using [http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN425](http://www.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN425) as one of my guides and I realize it is a bit dated as the kernel is 2.6.  Does this file still exist, is it in some other form?

Also, as an aside, I'd appreciate direction to any more kernel module programming.
i believe the package is called linux-doc

```
sudo apt-get install linux-doc
```

make sure you install dkms for kernel module hacking

---

### Post by Bad.Wulf on 2012-11-04
Excellent, thank you good sir!  That is exactly what I needed.  Can't imagine why packaging the documentation with the kernel is not default.  

Also, thanks for the heads up on dkms, I have it installed, looks very useful; like it solved a problem I was going to encounter soon :)

---

### Post by idoitprone on 2012-11-05
> **Bad.Wulf said:**
> Excellent, thank you good sir!  That is exactly what I needed.  Can't imagine why packaging the documentation with the kernel is not default.  

Also, thanks for the heads up on dkms, I have it installed, looks very useful; like it solved a problem I was going to encounter soon :)

it is a waste of space. not everyone is a kernel developer

It is simple to get module info with modinfo command

```
modinfo moduleName
```

---

