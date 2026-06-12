---
title: "Stuck at &quot;Loading initial ramdisk&quot; after kernel upgrade"
date: 2015-04-20
forum: General Help
---

### Post by h.hittini on 2015-04-20
Hi,

I have a fresh install of Ubuntu Server 13.10, it uses kernel 3.11 by default
I need to install this kernel [https://github.com/multipath-tcp/mptcp/tree/mptcp_v0.88](https://github.com/multipath-tcp/mptcp/tree/mptcp_v0.88)
I used the following command to prepare the config file
```
cp /boot/config-3.11.0-12-generic .config
```
I used "make menuconfig" after that to mark three more options and then compiled and installed the kernel as follows
```

make -j4
make modules_install
make install

```
When I try to boot to the new kernel it gets stuck at "Loading initial ramdisk"
I tried the following, I didn't get any errors but none of them worked
```

sudo update-initramfs -k 3.11.10mptcp -c
sudo grub-install /dev/sda
sudo update-grub

```
I tried booting using the recovery mode and choosing "root" to drop to root shell prompt and that worked fine
What's wrong here?

Thank you

---

### Post by h.hittini on 2015-04-20
It appears that there was an issue with my setup, I was testing the kernel in a virtual machine (parallels)
I tried installing the new kernel in a desktop and it worked fine

---

