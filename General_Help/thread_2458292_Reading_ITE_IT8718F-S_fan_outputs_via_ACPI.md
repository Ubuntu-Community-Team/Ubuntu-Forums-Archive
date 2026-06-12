---
title: "Reading ITE IT8718F-S fan outputs via ACPI"
date: 2021-02-20
forum: General Help
---

### Post by bcschmerker on 2021-02-20
**I need a lead for a situation with an *e*machines**®**/ac*e*r**®** EL1210-09 concerning the planar ITE**®** IT8718F-S at I/O Address 0x0290:**  I've run into an address-bus conflict attempting to load it87.ko in either LinUX Kernel 5.4.0-*nn*-generic or 5.8.0-*nn*-generic.  From the System Log:
```
ACPI Warning: SystemIO range 0x000000000000295-0x000000000000296 conflicts with OpRegion 0x000000000000295-0x000000000000296 (\IP) (20200528/utaddress-204)
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver.

```*Rarely* does it87.ko actually load; most attempts, /usr/sbin/modprobe throws a "Device or resource busy" error.  Neither the GNOME Shell Extension SysMon (which complains "Please install lm-sensors" in the FAN tab's source field) nor Psensor has input for the CPU Fan RPM as of 20 February 2021, and I already have lm-sensors installed.  How do I configure the appropriate package(s) among lmsensors, psensor, and/or gnome-shell-extension-sysmon so that the CPU fan RPM is available to any/all?

---

### Post by Yellow Pasque on 2021-02-21
You can use a newer version of it87 which has ignore_resource_conflict option.

```
sudo apt-get install build-essential dkms git
cd ~/ && mkdir source && cd source/
git clone https://github.com/a1wong/it87.git
cd it87/
sudo make dkms
sudo modprobe -v it87 ignore_resource_conflict=1
sensors
```

If it worked and you want to make it permanent:
```
echo "options it87 ignore_resource_conflict=1" | sudo tee -a /etc/modprobe.d/it87.conf
echo it87 | sudo tee -a /etc/modules
```

---

### Post by bcschmerker on 2021-02-22
**No dice - I had to turn ACPI off in the Kernel before *either* it87.ko would load.**  ACPI appears necessary for the system to power down at end of shutdown sequence.

---

### Post by luca-dgh on 2021-09-01
May be can be useful, in AUR (Archilinux User Repos) I found an actualized version of it87 driver that works kernel 5.4.0 [this is the link ]("https://aur.archlinux.org/packages/it87-dkms-git"). I installed it and works fine on Ubuntu 20.04 kernel 5.4.0-81.

---

### Post by bcschmerker on 2021-12-30
> **luca-dgh said:**
> May be can be useful, in AUR (Archilinux User Repos) I found an actualized version of it87 driver that works kernel 5.4.0 [this is the link ]("https://aur.archlinux.org/packages/it87-dkms-git"). I installed it and works fine on Ubuntu 20.04 kernel 5.4.0-81.

**Update:**  I'm also running Kernels 5.11.0-*-generic and 5.13.0-*-generic in addition to 5.4.0-*-generic; having a hard time downloading patched it87 source to /usr/local from GitHub so I CAN build the Kernel Object binary.

---

