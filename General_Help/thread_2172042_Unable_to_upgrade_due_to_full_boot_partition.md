---
title: "Unable to upgrade due to full /boot partition"
date: 2013-09-03
forum: General Help
---

### Post by RAND0M1ZER on 2013-09-03
I've had a similar issue before with /boot filling up but now I'm getting a new problem with dependencies. When I try to perform an upgrade I get this:

```

administrator@Server:~$ sudo apt-get upgrade
[sudo] password for administrator:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-server : Depends: linux-headers-3.2.0-43-generic but it is not in                                           stalled
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.43.51 is                                            installed
E: Unmet dependencies. Try using -f.

```

Using the -f flag, it proceeds normally but then stops with this error:

```

Unpacking linux-image-3.2.0-52-generic (from .../linux-image-3.2.0-52-generic_3.2.0-52.78_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-52-generic_3.2.0-52.78_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/config-3.2.0-52-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-52-generic /boot/vmlinuz-3.2.0-52-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-52-generic /boot/vmlinuz-3.2.0-52-generic
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.10 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.12_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-52-generic_3.2.0-52.78_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I followed this: [http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)

but I am getting an error when I try to remove packages like in that thread.

```


administrator@Server:~$ sudo apt-get remove linux-image-3.2.0-24-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-server : Depends: linux-headers-3.2.0-43-generic but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.43.51 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Impavidus on 2013-09-03
Your /boot partition is full, so you can't install a new kernel. The solution is that you uninstall some old kernels and then install the new. However, you can't uninstall old kernels as long as the package system is in an inconsistent state and the only way to make it consistent is completing the installation of the new headers or kernel. In other words, the deadlock you just encountered.

Try removing some files with old version numbers (like 3.2.0-24) from /boot manually using **rm**, then run **sudo apt-get -f install** and then properly uninstall the packages of which you removed a few files and any other old stuff you can miss. Just keep one old kernel.

---

### Post by RAND0M1ZER on 2013-09-03
Thanks for the reply. So I removed some old files manually from /boot using rm but when I run **sudo apt-get -f install **I get this,

```


administrator@Server:/boot$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-37-generic linux-image-3.2.0-38-generic linux-image-3.2.0-39-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-server linux-image-3.2.0-52-generic linux-image-server linux-server
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-52-generic
The following packages will be upgraded:
  linux-headers-server linux-image-server linux-server
3 upgraded, 1 newly installed, 0 to remove and 160 not upgraded.
9 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 150 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libapt-pkg4.12
```

I then tried removing or installing that file with apt-get but it didn't work

---

### Post by RAND0M1ZER on 2013-09-07
bump

---

