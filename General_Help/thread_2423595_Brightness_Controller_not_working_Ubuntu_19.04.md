---
title: "Brightness Controller not working Ubuntu 19.04"
date: 2019-07-25
forum: General Help
---

### Post by CalamityX on 2019-07-25
Brightness controller not workin with nvidia card. 
gpu manager printed:


last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-20-generic/updates/dkms
Found nvidia module: nvidia-uvm.ko
Looking for amdgpu modules in /lib/modules/5.0.0-20-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:1c20
BusID "PCI:1@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 1
I couldn't open /var/lib/ubuntu-drivers-common/last_gfx_boot for writing.
Error: can't write to /var/lib/ubuntu-drivers-common/last_gfx_boot

---

