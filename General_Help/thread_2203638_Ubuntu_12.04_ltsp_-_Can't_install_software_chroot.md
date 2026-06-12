---
title: "Ubuntu 12.04 ltsp - Can't install software chroot"
date: 2014-02-04
forum: General Help
---

### Post by vimets on 2014-02-04
Hi there all.
I have installed and configured an LTSP environment with ubuntu 12,04 and the problem that i have is that i have to install the apps in the server in order to see them once i'm loggued in.
If I do the typical chroot to /opt/ltsp/i386 and then install any app, like apt-get install geogebra, i don't see it in the client. However, if I do the installation out of the chroot, then I see the app, and i don't have to rebuild the image neither, kinda hot-swap with this.
i would like to have the "normal" environment with client images with diferent software.
Thanks

```
root@ltspserver:~# ltsp-info
server information:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

server packages:
ii ldm-server 2:2.2.9-1ubuntu0.1
ii ltsp-server 5.3.7-0ubuntu2.7
un ltsp-utils <none>
ii ltspfs 1.1-2

packages in chroot: /opt/ltsp/i386
un ldm <none>
un ldm-themes <none>
ii ldm-ubuntu-theme 2:2.0.47
un ldm-ubuntu-themes <none>
ii ltsp-client 5.3.7-0ubuntu2.6
un ltsp-client-core <none>
ii ltspfsd 1.1-2
un ltspfsd-core <none>

found: /opt/ltsp/i386/etc/lts.conf

found image: /opt/ltsp/images/i386.img
```

---

