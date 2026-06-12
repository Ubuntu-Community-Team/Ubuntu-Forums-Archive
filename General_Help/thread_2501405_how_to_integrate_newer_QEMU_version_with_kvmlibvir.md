---
title: "how to integrate newer QEMU version with kvm/libvirt/virt-manager"
date: 2024-10-05
forum: General Help
---

### Post by taguely on 2024-10-05
i've been using the virtual machine manager (aka `virt-manager`) in linux mint for quite a while, and i've come to learn that the instructions i followed ([https://documentation.ubuntu.com/server/how-to/virtualisation/virtual-machine-manager](https://documentation.ubuntu.com/server/how-to/virtualisation/virtual-machine-manager)) results in installation of packages via apt that are extremely outdated (qemu 6.2, dating to 2021, rather than the current qemu 9.1).  i tried removing the apt version of qemu and installing in other ways, but there seem to be dependencies with virt-manager and kvm that keep trying to pull in the old version.  after failing to get them to play nicely together, i uninstalled 9.1 and went back to the outdated version from apt.

my question: is there any way to integrate qemu 9.1 along with kvm and virt-manager to be able to leverage the many new features that qemu has rolled out in the past three years?

---

### Post by &amp;KyT$0P# on 2024-10-06
> **taguely said:**
> i tried removing the apt version of qemu and installing in other ways,

What "other ways" have you tried?

---

### Post by ian-weisser on 2024-10-06
qemu 6.2 from the Ubuntu repos  = Ubuntu 22.04.

Generally, Debian-based systems use snapshot-based approach to versions and dependencies. That's why it's extremely difficult to bolt new software onto an older release -- the dependencies often cannot be satisfied without radical surgery resulting in a sad, short-lived [Frankensystem]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian").

If you are using Ubuntu 22.04 repositories, then your snapshot is indeed from around December 2021.

Newer releases of qemu went into newer snapshots of Ubuntu. For example, Ubuntu 24.04 has qemu 8.2. Ubuntu 24.10 will have qemu 9.0

---

### Post by taguely on 2024-10-06
installing from the provided tarball and from raw git source.  those are  both limited to qemu though, so there is no guidance available on how  to make any needed changes to libvirtd or virt-manager.

---

### Post by taguely on 2024-10-06
> **ian-weisser said:**
> qemu 6.2 from the Ubuntu repos  = Ubuntu 22.04.

Generally, Debian-based systems use snapshot-based approach to versions and dependencies. That's why it's extremely difficult to bolt new software onto an older release -- the dependencies often cannot be satisfied without radical surgery resulting in a sad, short-lived [Frankensystem]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian").

If you are using Ubuntu 22.04 repositories, then your snapshot is indeed from around December 2021.

Newer releases of qemu went into newer snapshots of Ubuntu. For example, Ubuntu 24.04 has qemu 8.2. Ubuntu 24.10 will have qemu 9.0


thank you. this is helpful to know.  i guess i just need to do an OS upgrade.

---

### Post by &amp;KyT$0P# on 2024-10-06
> **taguely said:**
> installing from the provided tarball and from raw git source.

I don't think this can work with the apt version of virt-manager.

To use a newer QEMU version built from source, you would probably need to try finding newer qemu (and maybe libvirt and virt-manager too) **source** packages (**not .debs**) from [Ubuntu]("https://packages.ubuntu.com/") or [Debian]("https://www.debian.org/distrib/packages#search_packages"), and compile them into .deb packages for your Ubuntu system version.  This process (with any package) has potential to quickly become a tricky rabbit hole of risking a broken OS, so if you don't already have a good sense of it...well, I wouldn't start with something as critical and multi-part as QEMU/virt-manager :P

An OS upgrade would be safer, and less involved for you to maintain long-term.

---

