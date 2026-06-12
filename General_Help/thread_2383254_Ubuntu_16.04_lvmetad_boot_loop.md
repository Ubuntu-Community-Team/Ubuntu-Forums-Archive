---
title: "Ubuntu 16.04 lvmetad boot loop"
date: 2018-01-22
forum: General Help
---

### Post by dexmah on 2018-01-22
[COLOR=#CCB9B3 !important][FONT=arial][COLOR=#CCB9B3 !important]Good day,[/COLOR]
[COLOR=#CCB9B3 !important]I upgraded from ubuntu 14.04 to 16.04. system has been working for a month now. system is only using ubuntu, used the erase function. partition was all done through live cd.[/COLOR]
[COLOR=#CCB9B3 !important]currently using image 4.4.0.109 with 4.4.0.108 as the secondary.[/COLOR]
[COLOR=#CCB9B3 !important]during the boot process, i am getting this error.[/COLOR]
lvmetad is not active yet; using direct activation during sysinit
/dev/mapper/ubuntu--vg-root:recovering journal
/dev/mapper/ubuntu--vg-root: clean, xxxxx/xxxxxx files, xxxxxx/xxxxxxxx blocks

[COLOR=#CCB9B3 !important]Did a search, the error should eventually lead to log in screen. however system now goes into a boot loop.[/COLOR]
[COLOR=#CCB9B3 !important]Performed recovery, did not work.  ran for about half hour before freezing.[/COLOR]
[COLOR=#CCB9B3 !important]currently using system with upstart having ignored mounts. disk appears to the full in gparted. but using disk usage analyzer system only has 9gb in use. out of the total 500gb[/COLOR]
[COLOR=#CCB9B3 !important]performed [/COLOR]
[COLOR=#EF4343 !important]sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get install gtkorphan

[COLOR=#CCB9B3 !important]also used bleachbit which cleaned a bit of space.[/COLOR]
[COLOR=#CCB9B3 !important]tired to do bootrepair however this was not possible as there are conflicts. dont know if this is due to upstart boot. bootrepair has been performed twice, giving me the option to reinstall grub.[/COLOR]
[COLOR=#CCB9B3 !important]attempted to remove the quiet splash to nomodeset, however the text on the screen was not recognizable and booting stopped at some point with a blinking cursor. [/COLOR]
[COLOR=#CCB9B3 !important]any help will be greatly appreciated. i am currently suspending my computer as i am not sure if it will boot again. [/COLOR]

[COLOR=#CCB9B3 !important]not sure what other info is needed.[/COLOR]
[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ sudo vgs -o +devices,lv_path[/COLOR]
[COLOR=#CCB9B3 !important] VG        #PV #LV #SN Attr   VSize   VFree  Devices           Path [/COLOR]
[COLOR=#CCB9B3 !important] ubuntu-vg   1   2   0 wz--n- 465.52g 48.00m /dev/sda5(0)      /dev/ubuntu-vg/root [/COLOR]
[COLOR=#CCB9B3 !important] ubuntu-vg   1   2   0 wz--n- 465.52g 48.00m /dev/sda5(118166) /dev/ubuntu-vg/swap_1[/COLOR]

[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ sudo lvmdiskscan[/COLOR]
[COLOR=#CCB9B3 !important]/dev/ubuntu-vg/root   [     461.59 GiB] [/COLOR]
[COLOR=#CCB9B3 !important]/dev/sda1             [     243.00 MiB] [/COLOR]
[COLOR=#CCB9B3 !important] /dev/ubuntu-vg/swap_1 [       3.89 GiB] [/COLOR]
[COLOR=#CCB9B3 !important] /dev/sda5             [     465.52 GiB] LVM physical volume[/COLOR]
[COLOR=#CCB9B3 !important] 1 disk[/COLOR]
[COLOR=#CCB9B3 !important] 2 partitions[/COLOR]
[COLOR=#CCB9B3 !important] 0 LVM physical volume whole disks
[/COLOR][COLOR=#CCB9B3 !important]1 LVM physical volume[/COLOR]
[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ df -h[/COLOR]
[COLOR=#CCB9B3 !important]Filesystem                   Size  Used Avail Use% Mounted on[/COLOR]
[COLOR=#CCB9B3 !important]udev                         1.9G  4.0K  1.9G   1% /dev[/COLOR]
[COLOR=#CCB9B3 !important]tmpfs                        384M  1.4M  383M   1% /run[/COLOR]
[COLOR=#CCB9B3 !important]/dev/mapper/ubuntu--vg-root  455G  7.6G  424G   2% /[/COLOR]
[COLOR=#CCB9B3 !important]none                         4.0K     0  4.0K   0% /sys/fs/cgroup[/COLOR]
[COLOR=#CCB9B3 !important]none                         5.0M  4.0K  5.0M   1% /run/lock[/COLOR]
[COLOR=#CCB9B3 !important]none                         1.9G   11M  1.9G   1% /run/shm[/COLOR]
[COLOR=#CCB9B3 !important]none                         100M     0  100M   0% /run/user[/COLOR]
[COLOR=#CCB9B3 !important]cgmfs                        100K     0  100K   0% /run/cgmanager/fs[/COLOR]
[COLOR=#CCB9B3 !important]/dev/sda1                    236M  114M  110M  51% /boot[/COLOR]
[COLOR=#CCB9B3 !important]tmpfs                        384M  4.0K  384M   1% /run/user/112[/COLOR]
[COLOR=#CCB9B3 !important]tmpfs                        384M   84K  384M   1% /run/user/1000[/COLOR][COLOR=#CCB9B3 !important]
dexmah@dexmah-satellite-c55:~$ apt-get install -f[/COLOR]
[COLOR=#CCB9B3 !important]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)[/COLOR]
[COLOR=#CCB9B3 !important]E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/COLOR]

[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ ls -la /boot[/COLOR]
[COLOR=#CCB9B3 !important]total 103066[/COLOR]
[COLOR=#CCB9B3 !important]drwxr-xr-x  5 root root     1024 Jan 22 11:26 .[/COLOR]
[COLOR=#CCB9B3 !important]drwxr-xr-x 24 root root     4096 Jan 10 12:30 ..[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root  1249330 Jan  7 13:29 abi-4.4.0-108-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root  1249330 Jan  9 17:28 abi-4.4.0-109-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root   190533 Jan  7 13:29 config-4.4.0-108-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root   190533 Jan  9 17:28 config-4.4.0-109-generic[/COLOR]
[COLOR=#CCB9B3 !important]drwxr-xr-x  5 root root     1024 Jan 22 02:28 grub[/COLOR]
[COLOR=#CCB9B3 !important]drwxr-xr-x  4 root root     1024 Jan  2 22:44 grub.bak[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root 39834879 Jan  9 21:20 initrd.img-4.4.0-108-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root 39835338 Jan 22 11:26 initrd.img-4.4.0-109-generic[/COLOR]
[COLOR=#CCB9B3 !important]drwx------  2 root root    12288 Dec 31 20:26 lost+found[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf[/COLOR]
[COLOR=#CCB9B3 !important]-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin[/COLOR]
[COLOR=#CCB9B3 !important]-rw-------  1 root root  3888874 Jan  7 13:29 System.map-4.4.0-108-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-------  1 root root  3888874 Jan  9 17:28 System.map-4.4.0-109-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-------  1 root root  7104496 Jan  7 13:29 vmlinuz-4.4.0-108-generic[/COLOR]
[COLOR=#CCB9B3 !important]-rw-------  1 root root  7104528 Jan  9 17:28 vmlinuz-4.4.0-109-generic[/COLOR]
[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ dpkg -l | grep linux-
[/COLOR][COLOR=#CCB9B3 !important]ii  linux-base                                           4.0ubuntu1                                   all          Linux image base package[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-firmware                                       1.157.14                                     all          Firmware for Linux kernel drivers[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-generic                                        4.4.0.109.114                                amd64        Complete Generic Linux kernel and headers[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-headers-4.4.0-108                              4.4.0-108.131                                all          Header files related to Linux kernel version 4.4.0[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-headers-4.4.0-108-generic                      4.4.0-108.131                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-headers-4.4.0-109                              4.4.0-109.132                                all          Header files related to Linux kernel version 4.4.0[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-headers-4.4.0-109-generic                      4.4.0-109.132                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-headers-generic                                4.4.0.109.114                                amd64        Generic Linux kernel headers[/COLOR]
[COLOR=#CCB9B3 !important]rc  linux-image-3.13.0-32-generic                        3.13.0-32.57                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]rc  linux-image-4.4.0-104-generic                        4.4.0-104.127                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-image-4.4.0-108-generic                        4.4.0-108.131                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-image-4.4.0-109-generic                        4.4.0-109.132                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-image-extra-4.4.0-108-generic                  4.4.0-108.131                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-image-extra-4.4.0-109-generic                  4.4.0-109.132                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-image-generic                                  4.4.0.109.114                                amd64        Generic Linux kernel image[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-libc-dev:amd64                                 4.4.0-109.132                                amd64        Linux Kernel Headers for development[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-oem-tools-4.13.0-1015                          4.13.0-1015.16                               amd64        Linux kernel version specific tools for version 4.13.0-1015[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-4.13.0-1015-oem                          4.13.0-1015.16                               amd64        Linux kernel version specific tools for version 4.13.0-1015[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-4.4.0-108                                4.4.0-108.131                                amd64        Linux kernel version specific tools for version 4.4.0-108[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-4.4.0-108-generic                        4.4.0-108.131                                amd64        Linux kernel version specific tools for version 4.4.0-108[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-4.4.0-109                                4.4.0-109.132                                amd64        Linux kernel version specific tools for version 4.4.0-109[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-4.4.0-109-generic                        4.4.0-109.132                                amd64        Linux kernel version specific tools for version 4.4.0-109[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-common                                   4.4.0-109.132                                all          Linux kernel version specific tools for version 4.4.0[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-oem                                      4.13.0.1015.18                               amd64        OEM Linux kernel tools[/COLOR]
[COLOR=#CCB9B3 !important]ii  linux-tools-virtual                                  4.4.0.109.114                                amd64        This package will always depend on the latest minimal generic kernel tools.[/COLOR]
[COLOR=#CCB9B3 !important]ii  syslinux-common                                      3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)[/COLOR]
[COLOR=#CCB9B3 !important]ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies[/COLOR]

[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ uname -r[/COLOR]
[COLOR=#CCB9B3 !important]4.4.0-109-generic[/COLOR]
[COLOR=#CCB9B3 !important]dexmah@dexmah-satellite-c55:~$ df -i[/COLOR]
[COLOR=#CCB9B3 !important]Filesystem                    Inodes  IUsed    IFree IUse% Mounted on[/COLOR]
[COLOR=#CCB9B3 !important]udev                          485980    489   485491    1% /dev[/COLOR]
[COLOR=#CCB9B3 !important]tmpfs                         491263    582   490681    1% /run[/COLOR]
[COLOR=#CCB9B3 !important]/dev/mapper/ubuntu--vg-root 30253056 308291 29944765    2% /[/COLOR]
[COLOR=#CCB9B3 !important]none                          491263      3   491260    1% /sys/fs/cgroup[/COLOR]
[COLOR=#CCB9B3 !important]none                          491263      6   491257    1% /run/lock[/COLOR]
[COLOR=#CCB9B3 !important]none                          491263     51   491212    1% /run/shm[/COLOR]
[COLOR=#CCB9B3 !important]none                          491263      3   491260    1% /run/user[/COLOR]
[COLOR=#CCB9B3 !important]cgmfs                         491263     14   491249    1% /run/cgmanager/fs[/COLOR]
[COLOR=#CCB9B3 !important]/dev/sda1                      62248    583    61665    1% /boot[/COLOR]
[COLOR=#CCB9B3 !important]tmpfs                         491263      7   491256    1% /run/user/112[/COLOR]
[COLOR=#CCB9B3 !important]tmpfs                         491263     44   491219    1% /run/user/1000

i will provide any more information as needed. thank you.[/COLOR][/FONT][/COLOR]

---

