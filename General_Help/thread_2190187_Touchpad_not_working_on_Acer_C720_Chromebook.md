---
title: "Touchpad not working on Acer C720 Chromebook"
date: 2013-11-26
forum: General Help
---

### Post by tk83 on 2013-11-26
The Acer C720 Chromebook runs really well with Ubuntu (installed with [Chrubuntu]("http://chromeos-cr48.blogspot.co.uk/2013/10/chrubuntu-for-new-chromebooks-now-with.html")) dual-booting with ChromeOS. The only problem is that there is no support for the touchpad in the default Ubuntu kernels. 

When installing Ubuntu 13.10 or newer the Chrubuntu script automatically downloads and compiles in some kernel patches from Chromium developer Benson Leung ([https://plus.google.com/+BensonLeung/posts/EJUSUudzHb3](https://plus.google.com/+BensonLeung/posts/EJUSUudzHb3)). Unfortunately this automatic process doesn't work for the 12.04 LTS:

[SIZE=3]**Get Acer C720 touchpad working in Chrubuntu 12.04 LTS**[/SIZE]
[B]
Building the kernel modules (once-off for each kernel version)[/B]
- Install Ubuntu 13.10 or later in a VM
- On VM: sudo apt-get dist-upgrade
- On VM: reboot so most recent kernel is running
- On VM: Run cros-haswell-modules.sh, which is part of the Chrubuntu installation scripts ([https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh](https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh))
- On VM: ```
mkdir ~/Download/chrome-kernel; cd ~/Download/chrome-kernel
apt-get download linux-headers-`uname -r` linux-headers-generic linux-image-`uname -r` linux-headers-3.11.0-13 # replace 3.11.0-13 with the uname -r output minus '-generic'
mykern=${1:-$(uname -r)}
mykernver=linux-$(echo $mykern | cut -d'-' -f 1)
cp /lib/modules/$mykern/kernel/drivers/platform/x86/chromeos_laptop.ko .
cp /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-core.ko .
cp /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-pci.ko .
cp /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-platform.ko .
```

**Installing the fixed kernel on the Chromebook**
- On Chromebook: transfer .deb and .ko files over from VM:~/Download/chrome-kernel to ~/Download/chrome-kernel
- On Chromebook: cd ~/Download/chrome-kernel; dpkg -i *.dpkg
- On Chromebook: reboot into the newly installed kernel
- On Chromebook: create a script apply_patched_modules.sh with these contents:```
#!/bin/bash

mykern=${1:-$(uname -r)}
mykernver=linux-$(echo $mykern | cut -d'-' -f 1)

sudo mv /lib/modules/$mykern/kernel/drivers/platform/x86/chromeos_laptop.ko /lib/modules/$mykern/kernel/drivers/platform/x86/chromeos_laptop.ko.orig
sudo cp chromeos_laptop.ko /lib/modules/$mykern/kernel/drivers/platform/x86/

sudo mv /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-core.ko /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-core.ko.orig
sudo mv /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-pci.ko /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-pci.ko.orig
sudo mv /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-platform.ko /lib/modules/$mykern/kernel/drivers/i2c/busses/i2c-designware-platform.ko.orig

sudo cp i2c-designware-*.ko /lib/modules/$mykern/kernel/drivers/i2c/busses/

sudo depmod -a $mykern
```
- On Chromebook: cd ~/Download/chrome-kernel; sudo ./apply_patched_modules.sh
- On Chromebook: Add the following to /etc/modules:
```
chromeos_laptop
i2c-designware-core
i2c-designware-pci
i2c-designware-platform
```
- On Chromebook: reboot to apply the new modules

---

### Post by krumbs on 2013-12-18
Hi,
Thanks for the detailed guide. Before I try this out, wanted to confirm couple of points:
I have two Chromebooks (the HP Chromebook 14 and Acer C710-2847). In the first, have upgraded the SSD to 128GB and dual booted with Chrubuntu (13.10, Kubuntu). Trackpad works fine. 
But need your help with the Acer - have flashed John Lewis' Coreboot and installed Linux Mint 16 (Petra), which is based on Ubuntu 13.10. 
Will your guide still work, or do I need to change any steps? And instead of using a VM for the first few steps, can I execute those directly in Petra?

Thanks a ton for you time!

---

### Post by tk83 on 2013-12-18
I guess it should work as Mint is fairly similar so it should work. You shouldn't need a VM. Post how you get on.

---

### Post by krumbs on 2013-12-18
Stuck on Step 3 itself. Downloaded the 'cros-haswell-modules.sh' file and ran it. Got the error pasted below. Not sure what to do next.
Does this script work only on Haswell processors? The Acer C710 has the older Celeron 847. Do you think that is the problem here? 
---------------
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/i2c/busses/i2c-designware-pcidrv.c b/drivers/i2c/busses/i2c-designware-pcidrv.c
|index 816cbd1..0c6771d 100644
|--- a/drivers/i2c/busses/i2c-designware-pcidrv.c
|+++ b/drivers/i2c/busses/i2c-designware-pcidrv.c
--------------------------
File to patch: 

--------------

---

### Post by tk83 on 2013-12-18
No I doubt it's the hardware. The problem is that patch can't find the find the file drivers/i2c/busses/i2c-designware-pcidrv.c where it expects it. Since that script works on Ubuntu 13.10 it's likely there is something different about Linux Mint. 

You can look through the script and run the commands in it individually to see where it goes wrong. Alternatively might be easier to just create a VM of Ubuntu 13.10 and use that. Good luck!

---

### Post by ilko.derez on 2014-01-04
Hey krumbs, just wondering if you had gotten the touchpad to work in Mint 16? Any problems with the audio?

---

### Post by jwb1092 on 2014-01-07
Hi ilko.derez, 

The problem is that the script downloads an older kernel source that is not in the repos. If you follow the instructions below, it should work. 
[URL="http://realityequation.net/installing-elementary-os-on-an-hp-chromebook-14"]
http://realityequation.net/installing-elementary-os-on-an-hp-chromebook-14[/URL]

---

### Post by yurfader on 2014-02-02
I just executed the script [https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh](https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh) in Xubuntu and everything worked out again. I did not have to perform any of the steps described. My system is Xubuntu 13.10.

---

### Post by Tethtibis on 2014-02-11
yurfader , that script worked almost effortlessly, and flawlessly for me on xubuntu 13.10. Thank you for pointing that out. :O)

---

### Post by TheFu on 2014-04-18
> **yurfader said:**
> I just executed the script [https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh](https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh) in Xubuntu and everything worked out again. I did not have to perform any of the steps described. My system is Xubuntu 13.10.

Ran that script on a newly installed 14.04 Chromebook C720, then rebooted. Touchpad is working.  I looked over the script - seems safe enough and should work regardless of the kernel, as far as I can tell. After every dist-upgrade that installs a new kernel, the script will probably be needed again.

```
$ uname -a
Linux c720 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

/etc/modules contains:
```
chromeos_laptop
i2c-designware-core
i2c-designware-pci
i2c-designware-platform

```

Reboot.
Then to get select/paste working, I manually run this after GUI logins:
```
synclient AreaRightEdge=850 &
synclient AreaLeftEdge=50 &
synclient TapButton1=1 &
synclient TapButton2=3 &
synclient TapButton3=2 &
synclient FingerHigh=10 &
synclient FingerLow=10 &

```

Thanks to everyone who made this easy!

---

### Post by layuser1 on 2014-04-25
new chrubunto makes touchpad work without any updates needed.

---

### Post by TheFu on 2014-04-25
For at least the last 2 months, chrubuntu has worked to make the touchpad work for 13.10, perhaps longer, but I didn't have a C720 prior to that point. That's great, if you like the partitioning and want to waste **any** storage with chromeOS.  OTOH, wiping the HDD and putting 14.04 fresh on the HDD, then running that script will let us have control over the partitioning AND have the touchpad drivers working.  No need to waste any storage with anything we'll never use (i.e. chromeOS).

---

### Post by barinov2000 on 2014-05-06
... and if you get curious and/or lazy, try Ubuntu based Bodhi Linux iso with custom kernel built just for c720:

beta: [http://sourceforge.net/projects/bodhilinux/files/3.0.0-beta/](http://sourceforge.net/projects/bodhilinux/files/3.0.0-beta/)
stable: [http://sourceforge.net/projects/bodhilinux/files/specialhardware/](http://sourceforge.net/projects/bodhilinux/files/specialhardware/)

---

### Post by nymusicman on 2014-06-12
I'm trying to install kxstudio on c720. It uses the 3.13 low latency kernel (just updated to 3.13.29). The script says it's choosing linux instead of 3.13 low latency. Should I just let it run? Should I modify the script in some way?

Thanks!

---

### Post by nymusicman on 2014-06-12
I'm trying to install kxstudio on c720. It uses the 3.13 low latency kernel (just updated to 3.13.29). The script says it's choosing linux instead of 3.13 low latency. Should I just let it run? Should I modify the script in some way?

Thanks!

---

### Post by hugegreenbug on 2014-08-21
> **barinov2000 said:**
> ... and if you get curious and/or lazy, try Ubuntu based Bodhi Linux iso with custom kernel built just for c720:

beta: [http://sourceforge.net/projects/bodhilinux/files/3.0.0-beta/](http://sourceforge.net/projects/bodhilinux/files/3.0.0-beta/)
stable: [http://sourceforge.net/projects/bodhilinux/files/specialhardware/](http://sourceforge.net/projects/bodhilinux/files/specialhardware/)

I have an an image for standard Ubuntu with all the c720 issues worked out here: [https://www.distroshare.com/distros/get/12/](https://www.distroshare.com/distros/get/12/) .  I've tried Bodhi Linux and it doesn't have all the issues worked out  such as: suspend, not all of the touchpad problems, graphics issues, etc ...

---

### Post by DesertShadow on 2014-12-16
The script seems to work well to install chrubuntu, but on the Chromebook HP 14 Intel  it not longer seems to wfix the touchpad

---

