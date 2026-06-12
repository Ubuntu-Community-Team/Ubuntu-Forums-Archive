---
title: "a problem occurred while installing linux-image-extra"
date: 2017-12-21
forum: General Help
---

### Post by therealcain on 2017-12-21
Hello,
Every time i booting my computer i get this message:
[IMG]https://i.imgur.com/K9yJiKR.png[/IMG]

and every time i installing something through the terminal i get this message: ( installing lua )
```
therealcain@therealcain-system:~$ sudo apt-get install lua5.2
[sudo] password for therealcain: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  codeblocks-common gir1.2-appindicator3-0.1 gir1.2-keybinder-3.0
  libcodeblocks0 linux-headers-4.13.0-16 linux-headers-4.13.0-16-generic
  linux-headers-4.13.0-17 linux-headers-4.13.0-17-generic
  linux-image-4.13.0-16-generic linux-image-4.13.0-17-generic
  linux-image-extra-4.13.0-16-generic linux-image-extra-4.13.0-17-generic
  python-gconf python-pexpect python-ptyprocess
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  lua5.2
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
3 not fully installed or removed.
Need to get 97.7 kB of archives.
After this operation, 361 kB of additional disk space will be used.
Get:1 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) artful/main amd64 lua5.2 amd64 5.2.4-1.1build1 [97.7 kB]
Fetched 97.7 kB in 0s (580 kB/s)
Selecting previously unselected package lua5.2.
(Reading database ... 319092 files and directories currently installed.)
Preparing to unpack .../lua5.2_5.2.4-1.1build1_amd64.deb ...
Unpacking lua5.2 (5.2.4-1.1build1) ...
Setting up linux-image-extra-4.13.0-21-generic (4.13.0-21.24) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-21-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-21-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lua5.2 (5.2.4-1.1build1) ...
update-alternatives: using /usr/bin/lua5.2 to provide /usr/bin/lua (lua-interpreter) in auto mode
update-alternatives: using /usr/bin/luac5.2 to provide /usr/bin/luac (lua-compiler) in auto mode
Processing triggers for man-db (2.7.6.1-2) ...
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.13.0-21-generic; however:
  Package linux-image-extra-4.13.0-21-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.13.0.21.22); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-extra-4.13.0-21-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's really bothering me, how can i fix that ?

I'm asking here because i don't want to mess up my computer, i have some important projects in it.

---

### Post by speartip on 2017-12-21
Try running in a terminal.
```
sudo dpkg --configure -a
```
Or
```
sudo apt-get -f install
```
See if that resolves your issue.

---

### Post by therealcain on 2017-12-21
> **speartip said:**
> Try running in a terminal.
```
sudo dpkg --configure -a
```
Or
```
sudo apt-get -f install
```
See if that resolves your issue.

I have run them both and i got errors:
```
therealcain@therealcain-system:~$ sudo dpkg --configure -a
[sudo] password for therealcain: 
Setting up linux-image-extra-4.13.0-21-generic (4.13.0-21.24) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-21-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-21-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.13.0-21-generic; however:
  Package linux-image-extra-4.13.0-21-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.13.0.21.22); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-extra-4.13.0-21-generic
 linux-image-generic
 linux-generic
therealcain@therealcain-system:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  codeblocks-common gir1.2-appindicator3-0.1 gir1.2-keybinder-3.0
  libcodeblocks0 linux-headers-4.13.0-16 linux-headers-4.13.0-16-generic
  linux-headers-4.13.0-17 linux-headers-4.13.0-17-generic
  linux-image-4.13.0-16-generic linux-image-4.13.0-17-generic
  linux-image-extra-4.13.0-16-generic linux-image-extra-4.13.0-17-generic
  python-gconf python-pexpect python-ptyprocess
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-4.13.0-21-generic (4.13.0-21.24) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-21-generic /boot/vmlinuz-4.13.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-21-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-21-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.13.0-21-generic; however:
  Package linux-image-extra-4.13.0-21-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.13.0.21.22); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-extra-4.13.0-21-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by speartip on 2017-12-21
"No space left on device" comes up twice there. You need to check that the partition your installing the kernel to isn't full.
If it is you maybe need to delete some old kernels and run those commands again.

---

### Post by therealcain on 2017-12-21
> **speartip said:**
> "No space left on device" comes up twice there. You need to check that the partition your installing the kernel to isn't full.
If it is you maybe need to delete some old kernels and run those commands again.

thanks !

I managed to remove it by following [this]("https://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu").

---

### Post by speartip on 2017-12-21
Glad you sorted it.
```
sudo apt autoremove && sudo apt autoclean
```
is good for cleaning up unneeded packages on your system. Your new Kernel should now install without issue.

---

