---
title: "package dependency issues, E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-11-06
forum: General Help
---

### Post by bradhaack on 2015-11-06
Trying to install openssh-server results in:
```
dt1:sudo apt-get install openssh-server

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-67-generic : Depends: linux-image-3.13.0-67-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-67-generic but it is not going to be installed
 openssh-server : Depends: openssh-sftp-server but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```
dt1:sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcompfaceg1 xemacs21-basesupport xemacs21-mulesupport
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-67-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-67-generic
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
3 not fully installed or removed.
Need to get 0 B/14.7 MB of archives.
After this operation, 32.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 600935 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-67-generic_3.13.0-67.110_i386.deb ...
Done.
Unpacking linux-image-3.13.0-67-generic (3.13.0-67.110) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-67-generic' to '/boot/vmlinuz-3.13.0-67-generic.dpkg-new': unexpected end of file or stream
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Running clean and autoclean seems to have fixed it.

sudo apt-get clean 
sudo apt-get autoclean 
sudo apt-get -f install

---

### Post by ian-weisser on 2015-11-07
Looking at your output, the problem was a single corrupted package. You also could have just 'clean'ed that one package.

'autoclean' does nothing when run after 'clean'...there is nothing left for autoclean to work with.

---

### Post by bradhaack on 2015-11-07
Is there some maintenance that should be done occasionally to prevent something like this?

---

### Post by ian-weisser on 2015-11-07
Preventative maintenance? Not really.
It's quite rare, and (in the cases I've seen here in the forums) likely due to a transmission error or interruption, not a lack of maintenance.
And, of course, you found an effective solution regardless of the cause.

---

