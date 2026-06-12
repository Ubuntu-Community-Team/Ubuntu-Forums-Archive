---
title: "Ubuntu 14.04.4 / 15.10 shutdown issue - SOLUTION"
date: 2016-04-01
forum: General Help
---

### Post by Dedamraz on 2016-04-01
Hey all,

I have been struggling with this for quite a while now since after performing a shutdown the system halts but does not power off; and if there are some more of you with the same issue, here's how to finally fix it!

Step 0: Update your BIOS (not crucial, but comes in handy)
Step 1: Under "Exit" tab in BIOS you should have an option named "OS Optimized Defaults" which you should enable.
Step 2: After you have enabled the OS Optimized Defaults, next action is to Load Default Settings (this is just above the OS Optimized Defaults in BIOS - Step 2)
Step 3: Save & Exit
Step 4: Upgrade your Kernel to 4.5:
[LIST]
x64
```
cd /tmp/

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-wily/linux-headers-4.5.0-040500_4.5.0-040500.201603140130_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-wily/linux-headers-4.5.0-040500-generic_4.5.0-040500.201603140130_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-wily/linux-image-4.5.0-040500-generic_4.5.0-040500.201603140130_amd64.deb

sudo dpkg -i *.deb
```
x32
```
cd /tmp/

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-wily/linux-headers-4.5.0-040500_4.5.0-040500.201603140130_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-wily/linux-headers-4.5.0-040500-generic_4.5.0-040500.201603140130_i386.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-wily/linux-image-4.5.0-040500-generic_4.5.0-040500.201603140130_i386.deb

sudo dpkg -i *.deb
```
[/LIST]
Step 5: Reboot (it is possible you'll have to power it down just this one more time via power button)
Step 6: Enjoy your fully operational shutdown / restart option on your laptop.

Note: This was made on Lenovo Ideapad 100; and has been confirmed via colleague using an ASUS (have no idea which model though...)

---

