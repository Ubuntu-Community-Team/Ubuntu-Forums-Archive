---
title: "help with live-build"
date: 2023-12-09
forum: General Help
---

### Post by paxtonpengin on 2023-12-09
so i'm trying to make my own linux distro*, and i've hit a road block: vmlinuz. i'm using lunar lobster on xubuntu btw. now what road block am i hitting? 404, because ubuntu decided to remove all "server" downloads behind something else. can someone help me.

---

### Post by deadflowr on 2023-12-09
Probably help to know what tools you are using to do this.

---

### Post by paxtonpengin on 2023-12-09
i'm only using live-build live-boot and live-config
i did have to change some settings (bc it defaulted to precise insted of lunar)
but thats it
the directory it redirected me to was: [http://archive.ubuntu.com/ubuntu/dists/lunar/main/installer-amd64/current/cdrom/vmlinuz](http://archive.ubuntu.com/ubuntu/dists/lunar/main/installer-amd64/current/cdrom/vmlinuz)
or something like that,

---

### Post by MAFoElffen on 2023-12-09
Not a valid url...

For Precise, that was Ubiquity. Lunar, ad newer is the newer Flutter installer, which uses Subiquity with the Snap 'ubuntu-desktop-installer'... More like the Server Installer (but not).

An ISO file, is an archive file. The instructions to create a custom LiveCD include uncompressing the ISO archive into it's directories > modify what you want, to re-compressing the archive back into an ISO file. Added to that with Flutter, was instructions to uncompress the snap > modifying > then re-compressing...

Just what are you trying to do, within those two methods?

---

### Post by paxtonpengin on 2023-12-09
all i did was change the config files so that it wouldn't give me a 404 (because precise pangolin is not in the archive). the only command i entered was lb build

---

### Post by MAFoElffen on 2023-12-09
Yes, because Precise was end-of-life in 2017!!! That was over 6 years ago. Things do not work that way any more. You are talking about Lunar, which is almost end of life now also. That is not how the repo's are laid out. And what is contained in the repo's are packages, not individual files. It you wanted individual files, then you might have better luck using debootstrap as your toolset.

You asked, I told you, that is not there,and that is not how that works... Beyond that, then you leave the realm of Ubuntu support right? With your own Distribution? The only way I know about these things, is that this is what I dabbled with back in 2012, with the Ama-Gi Project.

There are ways to chroot into your custom ISO build and create your own initramfs and vmlinux images just by installing the kernel and updating the initramfs...

Here: 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
[https://github.com/canonical/ubuntu-desktop-installer#build-and-dry-run-the-installer](https://github.com/canonical/ubuntu-desktop-installer#build-and-dry-run-the-installer)

There are also other ways available now a days to clone an installed system into an ISO to distribute it. Like how the new Desktop installer does (Lunar on) where it creates the layout, mounts it, then rsync's a system image into that structure...

Read up and try to understand the concepts of how that works... If you cannot understand those basic concepts of how things work, then I don't know how you are going to support your own Distro, which is your goal, right? I don't know how I can explain that differently to you.

Maybe someone else might how better luck explaining that to you.

That is where I  am going to leave you with that. I wish you the best of luck.

---

### Post by paxtonpengin on 2023-12-09
kthxbye

---

### Post by paxtonpengin on 2023-12-10
i've updated my system to 23.10, i dont think it'll work because the "server" images dont exist anymore. at least the legacy images. which i need because live-build needs vmlinuz from those images. thats all i need

---

### Post by tea for one on 2023-12-10
Just offering an alternative approach:-
[https://github.com/PJ-Singh-001/Cubic](https://github.com/PJ-Singh-001/Cubic)

---

### Post by MAFoElffen on 2023-12-10
You need to understand that vmlinuz itself, is just a symlink to the active vmlinuz-<version> file that gets built during the kernel install:
```

root@noble-d05:~# ls -l /boot
total 124475
-rw-r--r-- 1 root root    279321 Oct  6 12:03 config-6.5.0-9-generic
drwxr-xr-x 3 root root      4096 Dec 31  1969 efi
drwxr-xr-x 5 root root         8 Dec 10 10:47 grub
lrwxrwxrwx 1 root root        26 Nov 28 14:26 initrd.img -> initrd.img-6.5.0-9-generic
-rw-r--r-- 1 root root 110100323 Dec 10 10:47 initrd.img-6.5.0-9-generic
lrwxrwxrwx 1 root root        26 Nov 28 14:26 initrd.img.old -> initrd.img-6.5.0-9-generic
-rw-r--r-- 1 root root    138712 Aug 19 03:40 memtest86+ia32.bin
-rw-r--r-- 1 root root    139776 Aug 19 03:40 memtest86+ia32.efi
-rw-r--r-- 1 root root    148440 Aug 19 03:40 memtest86+x64.bin
-rw-r--r-- 1 root root    149504 Aug 19 03:40 memtest86+x64.efi
-rw------- 1 root root   8513908 Oct  6 12:03 System.map-6.5.0-9-generic
lrwxrwxrwx 1 root root        23 Nov 28 14:26 vmlinuz -> vmlinuz-6.5.0-9-generic
-rw------- 1 root root  14271880 Oct  6 12:14 vmlinuz-6.5.0-9-generic
lrwxrwxrwx 1 root root        23 Nov 28 14:26 vmlinuz.old -> vmlinuz-6.5.0-9-generic

```
For example above, vmlinuz-6.5.0-9-generic would be regenerated if you reinstalled Linux kernel linux-image-6.5.0-9, which at the end of that process, it would update the symlinks, of vmilnuz and vmlinuz.old... The same with the symlinks to initrd.img & initrd.img.old. Then it would update-initramfs for that kernel.

That is how those files are built for, and during an install. That is how those files are created. "That is how that works". That is how those files point to the current kernel executable, and it's intramfs files image, for the boot loader to load.

---

