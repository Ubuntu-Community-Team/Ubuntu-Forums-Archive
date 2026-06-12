---
title: "Booting Problem on newly installed Ubuntu 18.04 Gnome desktop"
date: 2018-07-22
forum: General Help
---

### Post by satimis on 2018-07-22
Hi all,

CPU AMD-8 Core
RAM 32G onboard
HD - 2TB SSD (Samsung 860 EVO)

This is a newly installed HD.  The PC has been running at least 10 years without problem.

It takes about 45 sec booting up to Login but no GRUB boot loader menu popup.

On BIOS 
Booting Options```

ubuntu (P5: Samsung SSD 860 EVO 2TB)
UEFI (P5: Samsung SSD 860 EVO 2TB)
ubuntu (P5: Samsung SSD 860 EVO 2TB)
P5: Sony DVD
P4: Samsung SSD 860 EVO 2TB

```

I can boot either;
ubuntu (P5: Samsung SSD 860 EVO 2TB)
or
UEFI (P5: Samsung SSD 860 EVO 2TB)

but not;
P4: Samsung SSD 860 EVO 2TB (it requires a booting device).  I can't resolve why "ubuntu (P5: Samsung SSD 860 EVO 2TB)" appears twice.

Is it the BIOS of the motherboard out-of-date needing UEFI to replace it at booting?  This is my first time seeing this option.

$ df -kh```

Filesystem                   Size  Used Avail Use% Mounted on
udev                          16G     0   16G   0% /dev
tmpfs                        3.2G  1.9M  3.2G   1% /run
/dev/mapper/ubuntu--vg-root  1.8T  774G  965G  45% /
tmpfs                         16G   54M   16G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                         16G     0   16G   0% /sys/fs/cgroup
/dev/loop0                   141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop4                    15M   15M     0 100% /snap/gnome-logs/37
/dev/loop3                   1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop1                    13M   13M     0 100% /snap/gnome-characters/103
/dev/loop2                    35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop5                    21M   21M     0 100% /snap/gnome-logs/25
/dev/loop6                   141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop7                    87M   87M     0 100% /snap/core/4917
/dev/loop8                   3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop9                   2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop10                   13M   13M     0 100% /snap/gnome-characters/69
/dev/loop11                   87M   87M     0 100% /snap/core/4486
/dev/loop12                  3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/sda1                    511M  4.7M  507M   1% /boot/efi
tmpfs                        3.2G   16K  3.2G   1% /run/user/120
tmpfs                        3.2G   32K  3.2G   1% /run/user/1000

```

Why there are so many loops?

Please advise.  Also how to get GRUB boot loader menu back.  Thanks in advance


Edit
====

I got the GRUB bootloader menu back as follows;

Edit /etc/default/grub
Add a '#' at the beginning of following line```

GRUB_HIDDEN_TIMEOUT=0

```

Then run;```

sudo update-grub

```

Reboot.

Now the GRUB bootloader menu displayed at boot

Regards
satimis

---

