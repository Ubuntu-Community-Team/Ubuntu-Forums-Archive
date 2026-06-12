---
title: "Custom Live CD"
date: 2005-09-25
forum: General Help
---

### Post by C J Pro on 2005-09-25
I want to create a Live CD based on my ubuntu computer's current setup.  Is there anyway I can do this using the hardware detection methods used on the regular live CD?

---

### Post by tomchuk on 2005-09-26
Follow the remastering instructions on the Wiki, and do some or all of the following:
1. Copy the contents of your home direcotry to /etc/skel on the LiveCD.
2. Do a dpkg --get-selections > installed.txt on your computer, and a dpkg --set-selections < installed.txt in the LiveCD chroot. Also do an `echo "kernel-image-2.6.10-5-686 hold" | dpkg --set-selections` to make sure apt doesn't try and upgrade your kernel.
3. Do an apt-get dselect-upgrade to install packages that were on your computer, but not on the liveCD.
4. Remove packages from the liveCD that you don't want.

Finish the remaster, and burn your CD.

---

### Post by mlomker on 2005-09-26
There's a package called **bootcd** that you might want to take a look at.

---

### Post by zubziro on 2005-10-06
I need help to replace kernel on live CD with my own i followed [remaster]("https://wiki.ubuntu.com/LiveCDCustomizationHowTo?highlight=%28livecd%29") guide, downloaded my own kernel but when I do make-kpkg I get:
-----------------------------
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
unable to get login information for username "zubziro" at /usr/lib/dpkg/controllib.pl line 60.
Compilation failed in require at /usr/bin/dpkg-architecture line 27.
/usr/share/kernel-package/rules:1651: *** Error. I do not know where the kernel image goes to [kimagedest undefined] The usual case for this is that I could not determine which arch or subarch tihs machine belongs to. Please specify a subarch, and try again..  Stop.
-----------------------------------
the point of it is to get loop-aes glued into live CD, couse I can't find ANY live cd with loop-aes enabled (and don't tell me Knoppix it does't support loop-aes multi key V3 mode)
PLZ someone help !!

---

