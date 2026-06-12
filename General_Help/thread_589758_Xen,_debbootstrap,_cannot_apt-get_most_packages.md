---
title: "Xen, debbootstrap, cannot apt-get most packages"
date: 2007-10-24
forum: General Help
---

### Post by SilkBC on 2007-10-24
I have a bit of a weird issue.  I installed a Ubuntu 7.10 server over the weekend and installed Xen using the Ubuntu packages.  I then created an Ubuntu 7.10 guest domain using "debbootstrap" which was successful.

When I booted into the guest domain, I noticed that the "/etc/apt/sources.list" only had one entry which was only for base system packages (SSH, shorewall etc.)  I was unable to find such other packages as "htop", "openvpn", etc.

I copied my sources.list from the host to the guest and performed an "apt-get upgrade" in the guest.  I saw all the package headers get downloaded (way more than previous), yet I am still unable to find/install those other packages i mention (and yes, I can find them on the host is I do "apt-cache search <PACKAGE_NAME>"

I am not sure if this has to do with the install being done via debbootstrap or if there is some other issue.  I have never installed a system that way before, so I have no reference.

Any ideas and suggestions are appreciated.

Thanks! :-)

-SilkBC

---

