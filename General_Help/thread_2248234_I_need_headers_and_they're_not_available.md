---
title: "I need headers and they're not available?"
date: 2014-10-13
forum: General Help
---

### Post by Habitual on 2014-10-13
I installed sysdig 0.1.89 using ```
curl -s https://s3.amazonaws.com/download.draios.com/stable/install-sysdig | sudo bash
``` on my Ubuntu 14.04.1 LTS host.
I see this during the install.
```
Loading new sysdig-0.1.89 DKMS files...
First Installation: checking all kernels...
Building for 3.0.0-12-server and 3.13.0-37-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.13.0-37-generic
```

I get this message running sysdig as root:
```
sysdig
error opening device /dev/sysdig0. Make sure you have root credentials and that the sysdig-probe module is loaded.
``` and seems to be related to the headers, I found this
[https://groups.google.com/forum/#!topic/sysdig/eMIKWeiBUNA](https://groups.google.com/forum/#!topic/sysdig/eMIKWeiBUNA)

uname -r shows
```
3.0.0-12-server
```


grep menuentry  /boot/grub/grub.cfg
```
menuentry 'Ubuntu, with Linux 3.2.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-server' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.18.8-xenU' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.18.8-xenU (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

```

ls -ld /usr/src/*headers*
```
drwxr-xr-x 24 root root 4096 Oct  9 16:22 /usr/src/linux-headers-3.13.0-37
drwxr-xr-x  7 root root 4096 Oct  9 16:22 /usr/src/linux-headers-3.13.0-37-generic
```

ls /lib/modules
```
2.6.18.8-xenU  3.0.0-12-server  3.13.0-37-generic
```

find /lib/modules | grep sysdig
```
/lib/modules/3.13.0-37-generic/updates/dkms/sysdig-probe.ko
```

insmod /lib/modules/3.13.0-37-generic/updates/dkms/sysdig-probe.ko
```
insmod: ERROR: could not insert module /lib/modules/3.13.0-37-generic/updates/dkms/sysdig-probe.ko: Invalid module format
```

What must I do to use this invaluable utility?

Thanks for your time!

---

### Post by Habitual on 2014-10-14
Off-topic perhaps?

---

### Post by ian-weisser on 2014-10-15
Here are the available headers:

```
$ rmadison -u ubuntu linux-headers-generic
 linux-headers-generic | 2.6.32.21.22 | lucid            | amd64, i386
 linux-headers-generic | 2.6.32.67.74 | lucid-security   | amd64, i386
 linux-headers-generic | 2.6.32.67.74 | lucid-proposed   | amd64, i386
 linux-headers-generic | 2.6.32.67.74 | lucid-updates    | amd64, i386
 linux-headers-generic | 3.2.0.23.25  | precise          | amd64, i386
 linux-headers-generic | 3.2.0.70.84  | precise-security | amd64, i386
 linux-headers-generic | 3.2.0.70.84  | precise-proposed | amd64, i386
 linux-headers-generic | 3.2.0.70.84  | precise-updates  | amd64, i386
 linux-headers-generic | 3.13.0.24.28 | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-headers-generic | 3.13.0.37.44 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-headers-generic | 3.13.0.37.44 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-headers-generic | 3.13.0.38.45 | trusty-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-headers-generic | 3.16.0.22.23 | utopic           | amd64, arm64, armhf, i386, ppc64el
```

You can see the 3.13.0-37 is there.
But 3.0.0-12 has been long withdrawn.

One solution is to reboot into 3.13.0-37.

---

### Post by Habitual on 2014-10-15
> **ian-weisser said:**
> One solution is to reboot into 3.13.0-37. Yes, I considered that when I included the grub.cfg

I'm just not sure how.
```
ls -1 /boot | grep 3.13
abi-3.13.0-37-generic
config-3.13.0-37-generic
initrd.img-3.13.0-37-generic
System.map-3.13.0-37-generic
vmlinuz-3.13.0-37-generic
```

and bummer:
```
update-grub
GRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.
```

Stock minimal server install:
```
dpkg --get-selections | grep grub
grub-common                    install
grub-gfxpayload-lists                install
grub-pc                        install
grub-pc-bin                    install
grub2-common                    install
```



looking at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  now...

---

### Post by oldos2er on 2014-10-15
Moved to General Help.

---

