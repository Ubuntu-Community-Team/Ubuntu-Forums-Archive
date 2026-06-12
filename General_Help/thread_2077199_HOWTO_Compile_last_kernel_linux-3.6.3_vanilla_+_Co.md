---
title: "HOWTO Compile last kernel linux-3.6.3 vanilla + Con Kolivas patch - ubuntu/debian way"
date: 2012-10-28
forum: General Help
---

### Post by dentaku65 on 2012-10-28
Since my CPU do not support PAE and I need to works with up-to-date kernels (hardly provided by Team in the newer versions), here a simple How-To in order to create the kernel packages plus the Con Kolivas patch BFS for the kernel itself.

**Go in root shell:**
```
sudo -s
```
**Install needed packages:**
```
apt-get install git-core kernel-package fakeroot build-essential ncurses-dev
```
**Download Kernel and Con Kolivas patch:**
```
cd /usr/src
```
```
wget --continue http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.6.3.tar.bz2
```
```
wget http://ck.kolivas.org/patches/3.0/3.6/3.6-ck1/patch-3.6-ck1.bz2
```
**Unpack the Kernel and copy your config file:**
```
cd /usr/src
```
```
tar jxvf linux-3.6.3.tar.bz2
```
```
cd linux-3.6.3
```
```
cp /boot/config-`uname -r` ./.config
```
**Unpack Con Kolivas patch and versioning:**
```
cd /usr/src/linux-3.6.3
```
```
bzcat ../patch-3.6-ck1.bz2 | patch -p1
```
```
cd /usr/src
```
```
mv linux-3.6.3 linux-3.6.3-ck
```
```
cd linux-3.6.3-ck
```
[COLOR="Red"]***Modify your config***[/COLOR]
> I do not modified my current config file based on Ubuntu 12.04; in case you want to modify it, you must execute the command "**make menuconfig**" at this point, then save the operation. To do this you must be fully aware about your hardware components.
**Compile the Kernel (it takes quite while):**
```
cd /usr/src/linux-3.6.3-ck
```
```
make-kpkg clean
```
```
fakeroot make-kpkg --initrd --append-to-version=-vanilla kernel_image kernel_headers
```
> Note: After make-kpkg command above Con Kolivas BFS must be confirmed on console (Y by default) see [http://ck.kolivas.org/patches/bfs/bfs-configuration-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-configuration-faq.txt) for your box HZ options
> Note: After make-kpkg command above Kernel 3.6.3 asks a bunch of confirmations on console (Y|N choices); I've personally enter everything by the default ones, except for Android stuff (N by default, I choose Y)

**Verify and install the Kernel compiled:**
```
cd /usr/src
```
```
ls -al *.deb
```
> You'll list the 2 debs (image and headers)
```
dpkg -i *.deb
```
```
reboot
```

Done!

---

