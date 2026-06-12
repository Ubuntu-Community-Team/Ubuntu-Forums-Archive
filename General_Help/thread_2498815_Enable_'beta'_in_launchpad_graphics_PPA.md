---
title: "Enable 'beta' in launchpad graphics PPA?"
date: 2024-06-28
forum: General Help
---

### Post by yaminb on 2024-06-28
I currently use the ppa for nvidia drivers
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

However, sometimes I want to try one of the 'beta' or 'new feature' branch of the drivers. Is there a way to configure or change the PPA to allow it to get newer versions (beta).
My only alternative right now is to manually install the driver, which I don't like to do. I prefer going through the PPA.

The PPA is currently added as:
```

https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ 
noble
main

```
Thanks,

---

### Post by deadflowr on 2024-06-28
Currently the 555 driver in the PPA is the beta driver.

> Changelog
nvidia-graphics-drivers-555 (555.52.04-0ubuntu0~gpu20.04.2) focal; urgency=medium

  * New upstream beta release

 -- Rico Tzschichholz <ricotz@ubuntu.com>  Fri, 07 Jun 2024 23:44:34 +0200

---

### Post by yaminb on 2024-06-28
Yes, but how do i configure ubuntu to show that version in the propietary drivers in software updater. Mine shows the 5.45 version. I assume thats the prod version.

> 
sudo ubuntu-drivers list
nvidia-driver-545-open, (kernel modules provided by nvidia-dkms-545-open)
nvidia-driver-535-open, (kernel modules provided by linux-modules-nvidia-535-open-generic)
nvidia-driver-470-server, (kernel modules provided by linux-modules-nvidia-470-server-generic)
nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic)
nvidia-driver-470, (kernel modules provided by linux-modules-nvidia-470-generic)
nvidia-driver-545, (kernel modules provided by nvidia-dkms-545)
nvidia-driver-535-server-open, (kernel modules provided by linux-modules-nvidia-535-server-open-generic)
nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic)




---

### Post by deadflowr on 2024-06-29
>  how do i configure ubuntu to show that version in the propietary drivers in software updater. 
rewrite the scripts that ubuntu-drivers uses to determine the graphics card you have.
or
forsake using the software updater/ubuntu-drivers tool and go straight for the jugular and install it using apt directly.

---

