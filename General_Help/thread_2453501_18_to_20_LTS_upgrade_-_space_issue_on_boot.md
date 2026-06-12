---
title: "18 to 20 LTS upgrade - space issue on /boot"
date: 2020-11-11
forum: General Help
---

### Post by sniper8752 on 2020-11-11
I am getting this error message when doing my upgrade: 
```
[FONT=monospace][COLOR=#000000]Not enough free disk space  [/COLOR]

The upgrade has aborted. The upgrade needs a total of 132 M free  
space on disk '/boot'. Please free at least an additional 31.9 M of  
disk space on '/boot'. You can remove old kernels using 'sudo apt  
autoremove' and you could also set COMPRESS=xz in  
/etc/initramfs-tools/initramfs.conf to reduce the size of your  
initramfs. 
[/FONT]
```

I've already ran apt autoremove.  Here is what the /boot partition looks like: 
```
[FONT=monospace][COLOR=#000000]drwxr-xr-x  5 root root 1.0K Nov 11 14:22 [/COLOR][COLOR=#5454FF]**grub**[/COLOR][COLOR=#000000][/COLOR]
-rw-r--r--  1 root root  54M Nov 11 14:20 initrd.img-4.15.0-123-generic
-rw-r--r--  1 root root  42M Nov 11 14:19 initrd.img-4.4.0-194-generic
drwxr-xr-x 22 root root 4.0K Nov 11 14:18 [COLOR=#5454FF]**..**[/COLOR][COLOR=#000000][/COLOR]
-rw-------  1 root root 6.9M Nov 10 12:34 vmlinuz-4.4.0-194-generic
-rw-r--r--  1 root root 187K Oct 21 06:59 config-4.4.0-194-generic
-rw-------  1 root root 3.8M Oct 21 06:59 System.map-4.4.0-194-generic
-rw-------  1 root root 8.0M Oct 21 04:15 vmlinuz-4.15.0-123-generic
-rw-r--r--  1 root root 213K Oct 21 04:12 config-4.15.0-123-generic
-rw-------  1 root root 3.9M Oct 21 04:12 System.map-4.15.0-123-generic
drwx------  2 root root  12K Jan 14  2018 [COLOR=#5454FF]**lost+found**[/COLOR][COLOR=#000000][/COLOR]
-rw-r--r--  1 root root 179K Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root 181K Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root 181K Jan 28  2016 memtest86+_multiboot.bin

[/FONT][FONT=monospace][COLOR=#000000]df . -h[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       236M  129M   96M  58% /boot
[/FONT]
```

---

### Post by DuckHook on 2020-11-11
[LIST=1]
[*]Why a separate /boot partition and why so small?
[*]Where's the rest of your OS (i.e. where is /)?
[/LIST]
There's not much contextual info to go on here, but making a guess from the little there is, I would suggest that you back up your data and install a virgin system, this time, eliminating the tiny partitions for critical system resources. For most installs, there's really no need to hive off /boot into its own partition. Some people define a separate partition for /boot/efi, but no need to do that for /boot. If you have legitimate special circumstances that require a separate /boot (like ultra-hardened security provisions) then make it at least 1GB, preferably 2GB.

---

