---
title: "Suspend blues"
date: 2008-06-01
forum: General Help
---

### Post by astro4travel on 2008-06-01
I'm running Hardy Heron 8.04. Just recently I have been unable to bring my computer out of the suspend mode. I have to cut the power manually and then reboot. Quite the pain! This problem just started.  Prior to this the computer went into suspend mode just fine. Anyone else out there with this problem? Thanks, Michael

---

### Post by phidia on 2008-06-01
I have seen posts about this ( my laptop won't resume from suspend correctly in 7.10 either )
but the reason given for it happening with Heron is the kernel update-so for the time being booting using the previous kernel seems to be the fix.
See [this thread]("http://ubuntuforums.org/showthread.php?p=5087355#post5087355") for more on that.

---

### Post by sabme on 2008-06-01
I have exact same problem on my Sony VAIO C1Z.  Yesterday was all was fine, today after update, won't resume.  Forcing shutdown is not nice.

Big pain - pees me off - even though I love linux/ubuntu in principal. 

PLEASE FIX.

---

### Post by amit_ch on 2008-06-01
Hello,

I am on Ubuntu 7.10. After getting the last set of updates about 3-4 days, Hibernate no longer works.

Here is what no longer works means:
1. I click hibernate and it saves as usual.
2. When restarting next time, it reboots into the login screen. 
3. Now this time, if I select hibernate, it says no swap disk found and brings me back to the a locked desktop.

An interesting part, after step 2., free command shows swap is not present (0).
After restoring it (mkswap, update uuid in /etc/fstab and swapon), it comes back. But still fails.


Some noteworthy log entries
Jun  1 09:23:48 amit-laptop kernel: [    7.636000] EXT3-fs: sda3: orphan cleanup on readonly fs
Jun  1 09:23:48 amit-laptop kernel: [    7.636000] EXT3-fs: sda3: 4 orphan inodes deleted
Jun  1 09:23:48 amit-laptop kernel: [    7.636000] EXT3-fs: recovery complete.
Jun  1 09:23:48 amit-laptop kernel: [    7.652000] EXT3-fs: mounted filesystem with ordered data mode.

Everything in the /etc/grub.d/ directory except for 20_memtest86+ is gone.
amitch@amit-laptop:~$ uname -a
Linux amit-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

Please fix as a useful functionality was broken.

Thanks
Amit

---

### Post by Amarsingh0793 on 2008-06-01
Go to this thread and hopefully it will be fixed.

[http://ubuntuforums.org/showthread.php?p=2875529](http://ubuntuforums.org/showthread.php?p=2875529)

Good Luck!:)

---

### Post by amit_ch on 2008-06-01
The install list from last few updates, it is probably the one on May 30.

-----------------------
Commit Log for Fri May 30 20:28:23 2008
Upgraded the following packages:
libgnutls-dev (1.6.3-1build1) to 1.6.3-1ubuntu0.1
libgnutls13 (1.6.3-1build1) to 1.6.3-1ubuntu0.1
libgnutlsxx13 (1.6.3-1build1) to 1.6.3-1ubuntu0.1
linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.37) to 2.6.22-14.38
ssl-cert (1.0.14) to 1.0.14-0ubuntu0.7.10.1

Installed the following packages:
openssl-blacklist (0.1-0ubuntu0.7.10.4)
-----------------------
Commit Log for Sat May 24 10:59:02 2008
Upgraded the following packages:
ssl-cert (1.0.14) to 1.0.14-0ubuntu0.7.10.1

Installed the following packages:
openssl-blacklist (0.1-0ubuntu0.7.10.2)

-----------------------
Commit Log for Fri May 23 13:42:02 2008
Upgraded the following packages:
cupsys (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
cupsys-bsd (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
cupsys-client (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
cupsys-common (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
emacs (22.1-0ubuntu5.1) to 22.1-0ubuntu5.2
emacs22-bin-common (22.1-0ubuntu5.1) to 22.1-0ubuntu5.2
emacs22-common (22.1-0ubuntu5.1) to 22.1-0ubuntu5.2
emacs22-gtk (22.1-0ubuntu5.1) to 22.1-0ubuntu5.2
gstreamer0.10-esd (0.10.6-0ubuntu4) to 0.10.6-0ubuntu4.1
gstreamer0.10-plugins-good (0.10.6-0ubuntu4) to 0.10.6-0ubuntu4.1
kdelibs-data (4:3.5.8-0ubuntu3.3) to 4:3.5.8-0ubuntu3.4
kdelibs4-dev (4:3.5.8-0ubuntu3.3) to 4:3.5.8-0ubuntu3.4
kdelibs4c2a (4:3.5.8-0ubuntu3.3) to 4:3.5.8-0ubuntu3.4
kdelibs5 (3.94.0-0ubuntu1) to 3.94.0-0ubuntu1.1
kdelibs5-data (3.94.0-0ubuntu1) to 3.94.0-0ubuntu1.1
kdelibs5-dev (3.94.0-0ubuntu1) to 3.94.0-0ubuntu1.1
libcupsimage2 (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
libcupsys2 (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
libcupsys2-dev (1.3.2-1ubuntu7.6) to 1.3.2-1ubuntu7.7
libhsqldb-java (1.8.0.8-1ubuntu1) to 1.8.0.8-1ubuntu1.1
libspeex1 (1.1.12-3) to 1.1.12-3ubuntu0.7.10.1
libssl-dev (0.9.8e-5ubuntu3.1) to 0.9.8e-5ubuntu3.2
libssl0.9.8 (0.9.8e-5ubuntu3.1) to 0.9.8e-5ubuntu3.2
openoffice.org (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-base (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-calc (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-common (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-core (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-draw (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-evolution (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-gnome (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-gtk (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-impress (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-java-common (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-math (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-style-human (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openoffice.org-writer (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
openssh-client (1:4.6p1-5ubuntu0.2) to 1:4.6p1-5ubuntu0.5
openssl (0.9.8e-5ubuntu3.1) to 0.9.8e-5ubuntu3.2
python-uno (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
ssh-askpass-gnome (1:4.6p1-5ubuntu0.2) to 1:4.6p1-5ubuntu0.5
ssl-cert (1.0.14) to 1.0.14-0ubuntu0.7.10.1
thunderbird (2.0.0.12+nobinonly-0ubuntu0.7.10.0) to 2.0.0.14+nobinonly-0ubuntu0.7.10.0
ttf-opensymbol (1:2.3.0-1ubuntu5.3) to 1:2.3.0-1ubuntu5.4
update-manager (1:0.81.2) to 1:0.81.3
update-manager-core (1:0.81.2) to 1:0.81.3

Installed the following packages:
openssl-blacklist (0.1-0ubuntu0.7.10.2)

---

### Post by amit_ch on 2008-06-01
The package likely to have caused the problem is linux-ubuntu-modules-2.6.22-14-generic-2.6.22-14.38

Probably these changes,
  [Tim Gardner]

  * postinst does not run depmod correctly.
    - LP: #134193
  * depmod uses incorrect options in postinst and postrm
    - LP: #134193

I am going to rollback this package and see if it helps. Do not know, how to get grub files back though.

Amit

---

### Post by amit_ch on 2008-06-01
> **Amarsingh0793 said:**
> Go to this thread and hopefully it will be fixed.

[http://ubuntuforums.org/showthread.php?p=2875529](http://ubuntuforums.org/showthread.php?p=2875529)

Good Luck!:)

Amar,

That is a 2006 thread. It does not apply to this as Hibernate has been working well and without any hacks\changes for the last 2-3 distros.

Amit

---

### Post by amit_ch on 2008-06-01
Ok, rolling back to linux-ubuntu-modules-2.6.22-14-generic-2.6.22-14.37 did not fix it.

The grub files were always there, they are in /boot/grub/

There are no new kernels installed, so no kernel to rollback to.

I will wait I guess unless someone else finds something and before more slow in future upgrades.

Amit

---

