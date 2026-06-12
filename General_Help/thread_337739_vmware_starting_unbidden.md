---
title: "vmware starting unbidden"
date: 2007-01-13
forum: General Help
---

### Post by gwpritch on 2007-01-13
I have recently notice a considerable slowdown in my system. When I opened top I found that the vmware server daemon and vmware-vmx were running somewhere in the background consuming half of my resources. Why would this be happening and how do I stop it. 
Thanks.

---

### Post by haxer on 2007-01-13
killall vmware? :-k

---

### Post by gwpritch on 2007-01-13
yeah but how do I stop it from starting in the first place?

---

### Post by haxer on 2007-01-13
I have no idea ](*,)

---

### Post by gwpritch on 2007-01-13
Ok I got it sorted for anyone else who might experience a similar problem.
I originally used sysv-rc-conf to see which services were being started and vmware was listed but nothing was checked for any run level. However when I had a look in /etc/rc2.d vmware was indeed being started. So I justed renamed S90vmware to K90vmware and all is well.
Cheers all.

---

