---
title: "Ubuntu 15.04 apt-get fails for update"
date: 2015-09-12
forum: General Help
---

### Post by william_estrada on 2015-09-12
Hello group,
My newly installed Ubuntu 15.04 system has gotten into a failed state for aot-get.  Ant time a run apt-get, install, I get these error:```
apt-get install seamonkey\*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'seamonkey' for regex 'seamonkey*'
Note, selecting 'seamonkey-password-editor' for regex 'seamonkey*'
Note, selecting 'seamonkey-enigmail' for regex 'seamonkey*'
Note, selecting 'seamonkey-colorediffs' for regex 'seamonkey*'
Note, selecting 'seamonkey-y-u-no-validate' for regex 'seamonkey*'
Note, selecting 'seamonkey-pdf.js' for regex 'seamonkey*'
Note, selecting 'enigmail' instead of 'seamonkey-enigmail'
Note, selecting 'xul-ext-colorediffs' instead of 'seamonkey-colorediffs'
Note, selecting 'xul-ext-password-editor' instead of 'seamonkey-password-editor'
Note, selecting 'xul-ext-pdf.js' instead of 'seamonkey-pdf.js'
Note, selecting 'xul-ext-y-u-no-validate' instead of 'seamonkey-y-u-no-validate'
xul-ext-colorediffs is already the newest version.
xul-ext-password-editor is already the newest version.
xul-ext-pdf.js is already the newest version.
xul-ext-y-u-no-validate is already the newest version.
enigmail is already the newest version.
The following packages will be REMOVED:
  linux-image-extra-3.19.0-26-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 161 MB disk space will be freed.
Do you want to continue? [Y/n] y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US",
    LC_ALL = (unset),
    LC_CTYPE = "Cf",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 450817 files and directories currently installed.)
Removing linux-image-extra-3.19.0-26-generic (3.19.0-26.28) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-26-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic
grep: /boot/config-3.19.0-26-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_EaGM6r/lib/modules/3.19.0-26-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_EaGM6r/lib/modules/3.19.0-26-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Fatal: open /boot/vmlinuz-3.19.0-25-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-26-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.19.0-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Update works but upgrade, autoremove, install also fail.

What do I need to do to clear this up?

---

### Post by william_estrada on 2015-09-12
OK, I fixed the problem:```
apt-get --reinstall install  linux-image-3.19.0-25-generic
apt-get upgrade

```
For some reason, this broke grub and I need to reinstall grub-install?```
mount /dev/sda6 /sda6
grub-install --root-directory=/sda6 /dev/sda

```
Thanks for your time.

---

### Post by miryafa on 2015-11-17
I'm having the same problem, but 
```
apt-get --reinstall install  linux-image-3.19.0-25-generic 
apt-get upgrade
```
...failed for me. I just installed this off an Ubuntu Live CD, so I'm not sure what's going on. Can anyone offer any suggestions?

---

### Post by mörgæs on 2015-11-18
Are you sure you want to install 15.04 now? It's only supported a few months more. 
15.10 with support through July might be better choice.

---

