---
title: "apt-get check` failed, you may have broken packages. Aborting"
date: 2022-08-08
forum: General Help
---

### Post by Billisnice on 2022-08-08
Unpacking net-tools (1.60+git20181103.0eebece-1ubuntu5) ...
Setting up net-tools (1.60+git20181103.0eebece-1ubuntu5) ...
Processing triggers for man-db (2.10.2-1) ...
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.3.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...

How do I fix? Thanks

---

### Post by Bashing-om on 2022-08-08
Billisnice; Hey hey :D

Show us the results of:
```

sudo apt update
sudo apt full-upgrade

```

we see here what the package manager thinks.

[INDENT]If apt is not happy ......[/INDENT]

---

### Post by Billisnice on 2022-08-08
billn@billn-N107:~$ sudo apt update
[sudo] password for billn: 
Hit:1 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease                  
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]  
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [114 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [99.8 kB]
Fetched 324 kB in 1s (337 kB/s)                                     
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
billn@billn-N107:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  crda libssl1.1
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
billn@billn-N107:~$

---

### Post by oldos2er on 2022-08-08
Try installing the ones that have been kept back. I've seen this same problem reported by a few different Ubuntu users over the past week or so. ```
sudo apt install python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
```

---

### Post by Billisnice on 2022-08-08
bottom   `apt-get check` failed, you may have broken packages. Aborting...

billn@billn-N107:~$ sudo apt install python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
[sudo] password for billn: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  crda libssl1.1
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 142 kB of archives.
After this operation, 7,168 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 ubuntu-release-upgrader-gtk all 1:22.04.13 [9,132 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 ubuntu-release-upgrader-core all 1:22.04.13 [26.2 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 python3-distupgrade all 1:22.04.13 [107 kB]
Fetched 142 kB in 0s (317 kB/s)            
(Reading database ... 221417 files and directories currently installed.)
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a22.04.13_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:22.04.13) over (1:22.04.12) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a22.04.13_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:22.04.13) over (1:22.04.12) ...
Preparing to unpack .../python3-distupgrade_1%3a22.04.13_all.deb ...
Unpacking python3-distupgrade (1:22.04.13) over (1:22.04.12) ...
Setting up python3-distupgrade (1:22.04.13) ...
Setting up ubuntu-release-upgrader-core (1:22.04.13) ...
Setting up ubuntu-release-upgrader-gtk (1:22.04.13) ...
Processing triggers for man-db (2.10.2-1) ...
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.3.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...

---

### Post by oldos2er on 2022-08-09
So libdvd-pkg seems to be what it's choking on. Did you try removing it, or reinstalling? I'm not sure what would work.

---

### Post by Bashing-om on 2022-08-09
Billisnice; Hey

As above - let's see what we can find out about libdvd-pkg .
Post back - between code tags:>>  code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

```

apt policy libdvd-pkg 

```

see what we can do about cleaning/purging/re-installing the package (optional).

[INDENT]maybe yes
[/INDENT]

---

### Post by Billisnice on 2022-08-09
apt: command not found
billn@billn-N107:~$ apt policy libdvd-pkg
libdvd-pkg:
  Installed: 1.4.3-1-1
  Candidate: 1.4.3-1-1
  Version table:
 *** 1.4.3-1-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/multiverse amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/multiverse i386 Packages
        100 /var/lib/dpkg/status

---

### Post by Bashing-om on 2022-08-09
well well == all to the good

I had anticipated a PPA or such with the package ...

Let's try:
```

sudo apt clean
sudo apt --purge remove libdvd-pkg
sudo apt update
sudo apt install libdvd-pkg

```

This assumes that you want to be able to play video DVDs.
--where I do not:
> 
sysop@2004x-c:~$ apt policy libdvd-pkg
libdvd-pkg:
  Installed: (none)
  Candidate: 1.4.2-1-1
<snip>


the choice is yours to make :D

[INDENT]maybe Yes
[/INDENT]

---

### Post by Billisnice on 2022-08-09
n files for libdvd-pkg (1.4.3-1-1) ...
billn@billn-N107:~$ sudo apt install libdvd-pkg
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  crda libpcre2-32-0 libssl1.1
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libdvd-pkg
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 16.2 kB of archives.
After this operation, 84.0 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/multiverse amd64 libdvd-pkg all 1.4.3-1-1 [16.2 kB]
Fetched 16.2 kB in 0s (60.9 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libdvd-pkg.
(Reading database ... 221215 files and directories currently installed.)
Preparing to unpack .../libdvd-pkg_1.4.3-1-1_all.deb ...
Unpacking libdvd-pkg (1.4.3-1-1) ...
Setting up libdvd-pkg (1.4.3-1-1) ...
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reco
nfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] p
ostponed till after next APT operation.

---

### Post by Bashing-om on 2022-08-09
Billisnice; hummm ----

Did you take the package manager's advise and run:```

sudo dpkg-reconfigure libdvd-pkg
sudo apt update
sudo apt full-upgrade

```

what results ?

[INDENT]Maybe maybe now
[/INDENT]

---

### Post by Billisnice on 2022-08-09
```
$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  crda libpcre2-32-0 libssl1.1
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-5.15.0-46 linux-headers-5.15.0-46-generic
  linux-image-5.15.0-46-generic linux-modules-5.15.0-46-generic
  linux-modules-extra-5.15.0-46-generic
The following packages will be upgraded:
  linux-generic linux-generic-hwe-20.04 linux-generic-hwe-22.04
  linux-headers-generic linux-headers-generic-hwe-22.04 linux-image-generic
  linux-image-generic-hwe-22.04 linux-libc-dev snapd
9 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 137 MB of archives.
After this operation, 590 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-modules-5.15.0-46-generic amd64 5.15.0-46.49 [22.7 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-image-5.15.0-46-generic amd64 5.15.0-46.49 [11.4 MB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-modules-extra-5.15.0-46-generic amd64 5.15.0-46.49 [63.9 MB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-generic amd64 5.15.0.46.46 [1,702 B]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-image-generic amd64 5.15.0.46.46 [2,582 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-5.15.0-46 all 5.15.0-46.49 [12.3 MB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-5.15.0-46-generic amd64 5.15.0-46.49 [2,836 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-generic amd64 5.15.0.46.46 [2,436 B]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-generic-hwe-22.04 amd64 5.15.0.46.46 [1,668 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-image-generic-hwe-22.04 amd64 5.15.0.46.46 [2,604 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-generic-hwe-22.04 amd64 5.15.0.46.46 [2,468 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-generic-hwe-20.04 amd64 5.15.0.46.46 [1,660 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-46.49 [1,298 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 snapd amd64 2.56.2+22.04ubuntu1 [22.8 MB]
Fetched 137 MB in 13s (10.8 MB/s)                                              
Selecting previously unselected package linux-modules-5.15.0-46-generic.
(Reading database ... 221264 files and directories currently installed.)
Preparing to unpack .../00-linux-modules-5.15.0-46-generic_5.15.0-46.49_amd64.de
b ...
Unpacking linux-modules-5.15.0-46-generic (5.15.0-46.49) ...
Selecting previously unselected package linux-image-5.15.0-46-generic.
Preparing to unpack .../01-linux-image-5.15.0-46-generic_5.15.0-46.49_amd64.deb 
...
Unpacking linux-image-5.15.0-46-generic (5.15.0-46.49) ...
Selecting previously unselected package linux-modules-extra-5.15.0-46-generic.
Preparing to unpack .../02-linux-modules-extra-5.15.0-46-generic_5.15.0-46.49_am
d64.deb ...
Unpacking linux-modules-extra-5.15.0-46-generic (5.15.0-46.49) ...
Preparing to unpack .../03-linux-generic_5.15.0.46.46_amd64.deb ...
Unpacking linux-generic (5.15.0.46.46) over (5.15.0.43.44) ...
Preparing to unpack .../04-linux-image-generic_5.15.0.46.46_amd64.deb ...
Unpacking linux-image-generic (5.15.0.46.46) over (5.15.0.43.44) ...
Selecting previously unselected package linux-headers-5.15.0-46.
Preparing to unpack .../05-linux-headers-5.15.0-46_5.15.0-46.49_all.deb ...
Unpacking linux-headers-5.15.0-46 (5.15.0-46.49) ...
Selecting previously unselected package linux-headers-5.15.0-46-generic.
Preparing to unpack .../06-linux-headers-5.15.0-46-generic_5.15.0-46.49_amd64.de
b ...
Unpacking linux-headers-5.15.0-46-generic (5.15.0-46.49) ...
Preparing to unpack .../07-linux-headers-generic_5.15.0.46.46_amd64.deb ...
Unpacking linux-headers-generic (5.15.0.46.46) over (5.15.0.43.44) ...
Preparing to unpack .../08-linux-generic-hwe-22.04_5.15.0.46.46_amd64.deb ...
Unpacking linux-generic-hwe-22.04 (5.15.0.46.46) over (5.15.0.43.44) ...
Preparing to unpack .../09-linux-image-generic-hwe-22.04_5.15.0.46.46_amd64.deb 
...
Unpacking linux-image-generic-hwe-22.04 (5.15.0.46.46) over (5.15.0.43.44) ...
Preparing to unpack .../10-linux-headers-generic-hwe-22.04_5.15.0.46.46_amd64.de
b ...
Unpacking linux-headers-generic-hwe-22.04 (5.15.0.46.46) over (5.15.0.43.44) ...
Preparing to unpack .../11-linux-generic-hwe-20.04_5.15.0.46.46_amd64.deb ...
Unpacking linux-generic-hwe-20.04 (5.15.0.46.46) over (5.15.0.43.44) ...
Preparing to unpack .../12-linux-libc-dev_5.15.0-46.49_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.15.0-46.49) over (5.15.0-43.46) ...
Preparing to unpack .../13-snapd_2.56.2+22.04ubuntu1_amd64.deb ...
Unpacking snapd (2.56.2+22.04ubuntu1) over (2.55.5+22.04) ...
Setting up snapd (2.56.2+22.04ubuntu1) ...
snapd.failure.service is a disabled or a static unit not running, not starting i
t.
snapd.snap-repair.service is a disabled or a static unit not running, not starti
ng it.
Setting up linux-libc-dev:amd64 (5.15.0-46.49) ...
Setting up linux-headers-5.15.0-46 (5.15.0-46.49) ...
Setting up linux-headers-5.15.0-46-generic (5.15.0-46.49) ...
Setting up linux-headers-generic-hwe-22.04 (5.15.0.46.46) ...
Setting up linux-headers-generic (5.15.0.46.46) ...
Setting up linux-image-5.15.0-46-generic (5.15.0-46.49) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.15.0-43-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.15.0-43-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.15.0-46-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-46-generic
Setting up linux-modules-5.15.0-46-generic (5.15.0-46.49) ...
Setting up linux-modules-extra-5.15.0-46-generic (5.15.0-46.49) ...
Setting up linux-image-generic-hwe-22.04 (5.15.0.46.46) ...
Setting up linux-generic-hwe-22.04 (5.15.0.46.46) ...
Setting up linux-image-generic (5.15.0.46.46) ...
Setting up linux-generic (5.15.0.46.46) ...
Setting up linux-generic-hwe-20.04 (5.15.0.46.46) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.6+22.04.20220217-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for linux-image-5.15.0-46-generic (5.15.0-46.49) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-46-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-46-generic
Found initrd image: /boot/initrd.img-5.15.0-46-generic
Found linux image: /boot/vmlinuz-5.15.0-43-generic
Found initrd image: /boot/initrd.img-5.15.0-43-generic
Found linux image: /boot/vmlinuz-5.15.0-41-generic
Found initrd image: /boot/initrd.img-5.15.0-41-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
```

---

### Post by Bashing-om on 2022-08-09
Billisnice; Well !

All looks good to me *IF* you are not dual booting -

Reboot the system (new kernel) and let's see what we have

[INDENT]looks yessey[/INDENT]

---

### Post by Billisnice on 2022-08-10
I rebooted the system. What do I need to type in the terminal to see if fixed? Thanks

---

### Post by Bashing-om on 2022-08-10
Billisnice; Well ---

For assurance one can run terminal commands:
```

sudo apt -f install
sudo dpkg -C

```
where -f install returns of all zeros is expected and from dpkg just a return to prompt is a good thing.

[INDENT]we do like clean
[/INDENT]

---

### Post by Billisnice on 2022-08-10
All GOOD! Thanks...

---

### Post by Bashing-om on 2022-08-10
Billisnice - Great :D

If this matter is now concluded to your satisfaction; then

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT]up up and away
[/INDENT]

---

