---
title: "automatic updates config on Ubuntu 12.04"
date: 2013-06-06
forum: General Help
---

### Post by lylex on 2013-06-06
Our Ubuntu 12.04 machines at times get the kernel updated mysteriously, and on the next shutdown they won't reboot, and we have to roll back to a previous kernel in grub.

In looking at how our automatic updates are configured, the only things I see enabled are:
- "${distro_id}:${distro_codename}-security" in /etc/apt/apt.conf.d/50unattended-upgrades
- Update-Package-Lists "1"  in 10periodic

I'm guessing these are defaults.  Would either of these (especially the security updates) cause a new kernel to be installed?

Thanks....Lyle

---

### Post by matt_symes on 2013-06-06
Hi

> **lylex said:**
> Our Ubuntu 12.04 machines at times get the kernel updated mysteriously, and on the next shutdown they won't reboot, and we have to roll back to a previous kernel in grub.

In looking at how our automatic updates are configured, the only things I see enabled are:
- "${distro_id}:${distro_codename}-security" in /etc/apt/apt.conf.d/50unattended-upgrades
- Update-Package-Lists "1"  in 10periodic

I'm guessing these are defaults.  Would either of these (especially the security updates) cause a new kernel to be installed?

Thanks....Lyle

You need to look at the file /etc/apt/apt.conf.d/10periodic.
```
matthew-S206:/etc % less /etc/apt/apt.conf.d/10periodic
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
matthew-S206:/etc % 
```

There should be a cron job associated with this.

```
/etc/cron.daily/apt
```

It should download kernel updates i believe. You can always pin the kernel.

I would try to see why the new kernel is failing though as new kernels contain secuirty updates.

Kind regards

---

