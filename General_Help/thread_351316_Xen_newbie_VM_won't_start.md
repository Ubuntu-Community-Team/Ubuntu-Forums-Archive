---
title: "Xen newbie: VM won't start"
date: 2007-02-01
forum: General Help
---

### Post by adaniels on 2007-02-01
Hi,

I'm new to Xen. I've followed [>this tutorial<]("https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy") to get started. I had problems using mkinitramfs, so I used yaird instead. The Xen server is running perfectly, but the image won't boot.

The image file is located at /xen-images/diskimage-ubuntu.ext3 and I've used the loopback-mounted-file method.

The harddisk is '/dev/sda'. Partition '/dev/sda3' is the root partition, '/dev/sda1' is the extended partition, with '/dev/sda4' and '/dev/sda5' as logical partitions. '/dev/sda2' is the swap disk. All disks (except the swap of course) are formatted with reiserfs.
```
/dev/sda3             15727068   5093824  10633244  33% /
varrun                  968996       168    968828   1% /var/run
varlock                 968996         0    968996   0% /var/lock
procbususb              968996       144    968852   1% /proc/bus/usb
udev                    968996       144    968852   1% /dev
devshm                  968996         0    968996   0% /dev/shm
/dev/sda5             60595264    380000  60215264   1% /home
/dev/sda6             36699288    978300  35720988   3% /xen-images
```

The xen configuration file ' /etc/xen/ubuntu.cfg' looks as follows:
```
kernel = "/boot/xen0-linux-2.6.17-6-generic-xen0"
ramdisk = "/boot/initrd.img-2.6.17-6-generic-xen0"
builder='linux'
memory = 128
name = "ubuntu"
vcpus = 1
vif = [ 'bridge=xenbr0' ]
disk = [ 'file:/xen-images/diskimage-ubuntu.ext3,ioemu:sda,w' ]
root = "/dev/sda ro"

```

When I start the virtual machine I get the following error:
```
/bin/cat: /sys/block/sda/sda3/dev: No such file or directory
Waiting 1 seconds for /sys/block/sda/sda3/dev to show up
```

I've tried 'root="/dev/sda3"' as well, but with the same result.

I don't understand why the virtual machine is looking for sda3. Can anyone tell me what I'm doing wrong?

---

### Post by adaniels on 2007-02-02
Anyone?

---

