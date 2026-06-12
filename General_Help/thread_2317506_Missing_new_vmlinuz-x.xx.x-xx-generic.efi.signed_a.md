---
title: "Missing new vmlinuz-x.xx.x-xx-generic.efi.signed after kernel update"
date: 2016-03-17
forum: General Help
---

### Post by ocirne2 on 2016-03-17
I have installed **Ubuntu 14.04.4** on a PC with **UEFI** and **GPT**, choosing the **LVM** option.
After installation, I could see in the **/boot** directory that the installed kernel version was **3.19.0-51** and that there were also several other files with the same version.

A few days later I updated the system and, together with other package updates, also the kernel got updated to the version **3.19.0-56** .
Looking again at the **/boot** directory, I could see that there was a new set of files with version **3.19.0-56**, except for the **generic.efi.signed** that was missing:

[FONT=courier new]-rw-r--r--  1 root root  1271993 Feb 26 23:32 abi-3.19.0-51-generic
-rw-r--r--  1 root root  1272130 Mar 11 13:10 abi-3.19.0-56-generic
-rw-r--r--  1 root root   177808 Feb 26 23:32 config-3.19.0-51-generic
-rw-r--r--  1 root root   177808 Mar 11 13:10 config-3.19.0-56-generic
drwxr-xr-x  3 root root     4096 Jan  1  1970 efi/
drwxr-xr-x  6 root root     1024 Mar 16 08:17 grub/
-rw-r--r--  1 root root 20619855 Mar  7 13:35 initrd.img-3.19.0-51-generic
-rw-r--r--  1 root root 21025201 Mar 14 16:25 initrd.img-3.19.0-56-generic
drwx------  2 root root    12288 Mar  4 10:57 lost+found/
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3630758 Feb 26 23:32 System.map-3.19.0-51-generic
-rw-------  1 root root  3631082 Mar 11 13:10 System.map-3.19.0-56-generic
-rw-------  1 root root  6575024 Feb 26 23:32 vmlinuz-3.19.0-51-generic
-rw-------  1 root root  6576952 Mar  4 10:59 **vmlinuz-3.19.0-51-generic.efi.signed**
-rw-------  1 root root  6579344 Mar 11 13:10 vmlinuz-3.19.0-56-generic
[/FONT]
I ask myself why the file **vmlinuz-3.19.0-56-generic.efi.signed** has not been generated: maybe is something wrong in the configuration ?

Surfing the web for a solution, I could see that other people have always a **generic.efi.signed** file for every kernel version in the **/boot** directory.

Currently I can boot the PC in **EFI mode** with the new kernel, even if the corresponding **generic.efi.signed** file is missing. Why?

How can I fix my system, letting generate a new **generic.efi.signed** file when a kernel is updated ?

Many thanks!

---

### Post by yetimon_64 on 2016-03-17
To keep up to the latest kernel release for the signed 3.19 kernel images, check you have "linux-signed-generic-lts-vivid" package installed. It is a meta package that "... will always depend on the latest complete generic Linux kernel and headers. Signed with the Ubuntu EFI key" (the description is taken from synaptic package manager)

Sounds like the meta package is missing for what you want kept up to date.

---

### Post by ocirne2 on 2016-03-18
Many thanks yetimon_64, now it works!

---

