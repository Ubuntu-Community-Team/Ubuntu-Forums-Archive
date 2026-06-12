---
title: "Boot record full"
date: 2015-02-07
forum: General Help
---

### Post by johnke7cw2 on 2015-02-07
How do I remove some of the old updates in the boot record?

---

### Post by mörgæs on 2015-02-07
A first try is running 

```
sudo apt-get update
sudo apt-get dist-upgrade
<reboot>
sudo apt-get autoremove
```

After another reboot how does the boot menu look?

---

### Post by gordintoronto on 2015-02-07
In my experience, the easiest way is to install Synaptic Package Manager. Run it, and search for one of the old kernels (eg 0-55) and "completely remove" the three files which show up. Repeat until you're down to three or four kernel versions. Then run this command:
sudo update-grub

---

### Post by mörgæs on 2015-02-08
The idea behind autoremove is doing this automagically for all old kernels, keeping the latest and the second latest.

---

### Post by gordintoronto on 2015-02-08
> **mörgæs said:**
> The idea behind autoremove is doing this automagically for all old kernels, keeping the latest and the second latest.

I don't think autoremove will do that.

---

### Post by Bashing-om on 2015-02-08
@ gordintorontol Hello; a Bit of obligatory payback.
'autoremov' has been revamped to do that - with the later kernels :
```

sysop@1404mini:~$ ls -al /boot
total 1223772
drwxr-xr-x  4 root root       4096 Feb  1 11:38 .
drwxr-xr-x 25 root root       4096 Feb  1 11:38 ..
-rw-r--r--  1 root root    1164720 Dec  8 14:28 abi-3.13.0-43-generic
-rw-r--r--  1 root root    1164720 Dec 15 19:17 abi-3.13.0-44-generic
-rw-r--r--  1 root root    1164967 Jan 13 14:12 abi-3.13.0-45-generic
-rw-r--r--  1 root root     165745 Dec  8 14:28 config-3.13.0-43-generic
-rw-r--r--  1 root root     165748 Dec 15 19:17 config-3.13.0-44-generic
-rw-r--r--  1 root root     165748 Jan 13 14:12 config-3.13.0-45-generic
drwxr-xr-x  5 root root       4096 Feb  7 18:25 grub
drwxr-xr-x  5 root root       4096 Jun  9  2014 grub_backup
-rw-r--r--  1 root root   19331820 Dec 11 08:07 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root   19334071 Jan 12 20:22 initrd.img-3.13.0-44-generic
-rw-r--r--  1 root root   19344106 Feb  1 11:38 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root     176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root     178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root     178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root    3388760 Dec  8 14:28 System.map-3.13.0-43-generic
-rw-------  1 root root    3388834 Dec 15 19:17 System.map-3.13.0-44-generic
-rw-------  1 root root    3389258 Jan 13 14:12 System.map-3.13.0-45-generic
-rw-r-----  1 root root 1162936320 Jan 15 12:00 ubie1410.iso
-rw-------  1 root root    5814080 Dec  8 14:28 vmlinuz-3.13.0-43-generic
-rw-------  1 root root    5814496 Dec 15 19:17 vmlinuz-3.13.0-44-generic
-rw-------  1 root root    5814112 Jan 13 14:12 vmlinuz-3.13.0-45-generic
sysop@1404mini:~$ 

sysop@1404mini:~$ sudo apt-get autoremove
[sudo] password for sysop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 271 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 147910 files and directories currently installed.)
Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-headers-3.13.0-43 (3.13.0-43.72) ...
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda7
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sdc1
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdc2
done
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda7
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sdc1
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdc2
done
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /boot
total 1194596
drwxr-xr-x  4 root root       4096 Feb  8 20:25 .
drwxr-xr-x 25 root root       4096 Feb  1 11:38 ..
-rw-r--r--  1 root root    1164720 Dec 15 19:17 abi-3.13.0-44-generic
-rw-r--r--  1 root root    1164967 Jan 13 14:12 abi-3.13.0-45-generic
-rw-r--r--  1 root root     165748 Dec 15 19:17 config-3.13.0-44-generic
-rw-r--r--  1 root root     165748 Jan 13 14:12 config-3.13.0-45-generic
drwxr-xr-x  5 root root       4096 Feb  8 20:25 grub
drwxr-xr-x  5 root root       4096 Jun  9  2014 grub_backup
-rw-r--r--  1 root root   19334071 Jan 12 20:22 initrd.img-3.13.0-44-generic
-rw-r--r--  1 root root   19344106 Feb  1 11:38 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root     176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root     178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root     178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root    3388834 Dec 15 19:17 System.map-3.13.0-44-generic
-rw-------  1 root root    3389258 Jan 13 14:12 System.map-3.13.0-45-generic
-rw-r-----  1 root root 1162936320 Jan 15 12:00 ubie1410.iso
-rw-------  1 root root    5814496 Dec 15 19:17 vmlinuz-3.13.0-44-generic
-rw-------  1 roo

```
in this instance kernel -43 is gone gone.

[INDENT][INDENT]it be a chang'n
[/INDENT][/INDENT]

---

### Post by gordintoronto on 2015-02-09
Wow, thanks for the update!

---

