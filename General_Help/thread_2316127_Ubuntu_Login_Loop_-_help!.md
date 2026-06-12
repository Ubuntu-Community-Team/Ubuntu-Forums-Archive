---
title: "Ubuntu Login Loop - help!"
date: 2016-03-05
forum: General Help
---

### Post by villieb on 2016-03-05
hello everyone... Firstly I apologise if this is in the wrong section...

I carried out an update this morning and following the update the system asked me to reboot. I've rebooted and now stuck in a login loop (the resolution of the log in screen is also lower from the previous log in screen).

The same happens when I try and log in as guest.

I've done some research and carried out a few commands that I've found (reconfiguring and restarting lightdm, ensuring .Xauthority has the correct owners, re-installing ubuntu-desktop, installing gdm) but nothing seems to resolve the issue for me.

```

villieb@media-sever:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.6G  4.0K  3.6G   1% /dev
tmpfs           737M  1.4M  736M   1% /run
/dev/sda2        52G   38G   12G  77% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            3.6G  148K  3.6G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda1        94M  120K   94M   1% /boot/efi
/dev/md127      5.4T  2.7T  2.5T  52% /home/villieb/share

villieb@media-sever:~$ ls -al .Xauthority
-rw------- 1 villieb villieb 56 Mar  5 13:06 .Xauthority

villieb@media-sever:~$ ls -al .ICEauthority
-rw------- 1 villieb villieb 51484 Feb 17 10:02 .ICEauthority

villieb@media-sever:~$ sudo lshw -C display
[sudo] password for villieb:
  *-display
       description: VGA compatible controller
       product: Trinity [Radeon HD 7480D]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:17 memory:c0000000-cfffffff ioport:f000(size=256) memory:fef00000-fef3ffff
villieb@media-sever:~$

```

Can anyone help me try and troubleshoot further?

Thanks

---

### Post by villieb on 2016-03-09
No one...?

---

