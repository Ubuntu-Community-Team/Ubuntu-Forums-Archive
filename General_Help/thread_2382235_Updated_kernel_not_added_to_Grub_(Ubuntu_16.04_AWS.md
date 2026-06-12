---
title: "Updated kernel not added to Grub (Ubuntu 16.04 AWS instances)"
date: 2018-01-10
forum: General Help
---

### Post by ptader on 2018-01-10
I have several AWS instances that after upgrading to the latest Ubuntu kernel I noticed that it's not added to grub as the default kernel. In fact, it's not added to grub at all. ...and so it reboots with an older kernel. If I manually configure /boot/grub/menu.lst it does boot with the new kernel with no issues.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
```

It is also a paravirtual instances

I've run:
```
sudo apt-get clean
sudo apt-get dist-upgrade
```

```

The following NEW packages will be installed:
  linux-aws-headers-4.4.0-1048 linux-headers-4.4.0-1048-aws linux-image-4.4.0-1048-aws
```

I'm suspicious of these errors I see during the upgrade and also while running update-grub:

```
ubuntu@ip-172-20-46-197-dev:~$ sudo update-grub

Generating grub configuration file ...
grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.

...<snip>...

/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
Found linux image: /boot/vmlinuz-4.4.0-1048-aws
Found initrd image: /boot/initrd.img-4.4.0-1048-aws
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.

...<snip>...

/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
Found linux image: /boot/vmlinuz-4.4.0-1047-aws
Found initrd image: /boot/initrd.img-4.4.0-1047-aws
Found linux image: /boot/vmlinuz-4.4.0-1044-aws
Found initrd image: /boot/initrd.img-4.4.0-1044-aws
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
/usr/sbin/grub-probe: warning: disk does not exist, so falling back to partition device /dev/xvda1.
done

```


```
$ cat /etc/fstab
LABEL=cloudimg-rootfs	/	 ext4	defaults,discard	0 0
```


And the latest kernel is installed.

```
ubuntu@ip-172-20-46-35-dev:~$ dpkg -la |grep linux-image
rc  linux-image-4.4.0-1030-aws       4.4.0-1030.39                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1031-aws       4.4.0-1031.40                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1032-aws       4.4.0-1032.41                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1035-aws       4.4.0-1035.44                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1038-aws       4.4.0-1038.47                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1039-aws       4.4.0-1039.48                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1041-aws       4.4.0-1041.50                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-1043-aws       4.4.0-1043.52                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-1044-aws       4.4.0-1044.53                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-1047-aws       4.4.0-1047.56                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-1048-aws       4.4.0-1048.57                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-aws                  4.4.0.1048.50                              amd64        Linux kernel image for Amazon Web Services (AWS) systems.
```



I'm ok manually configuring Grub, but would rather not. Any thoughts?

Thanks everyone.

---

