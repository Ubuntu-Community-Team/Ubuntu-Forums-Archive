---
title: "Firefox v112.0.2 permisions with 2nd internal hard drive"
date: 2023-05-02
forum: General Help
---

### Post by pautorras on 2023-05-02
Hi Folks,

I have some problems with Firefox v112.0.2.
Firefox can't save files on the second internal hard drive.

In this case, Firefox was not installed by snap.

```

pau@pau-ThinkBook-16-G4-IAP:~$ snap list
Name                 Version          Rev    Tracking       Publisher       Notes
bare                 1.0              5      latest/stable  canonical&#10003;      base
canonical-livepatch  10.5.5           209    latest/stable  canonical&#10003;      -
core                 16-2.58.3        14946  latest/stable  canonical&#10003;      core
core20               20230308         1852   latest/stable  canonical&#10003;      base
core22               20230404         617    latest/stable  canonical&#10003;      base
gnome-3-38-2004      0+git.6f39565    140    latest/stable  canonical&#10003;      -
gnome-42-2204        0+git.587e965    99     latest/stable  canonical&#10003;      -
gtk-common-themes    0.1-81-g442e511  1535   latest/stable  canonical&#10003;      -
pinta                2.1.1            25     latest/stable  james-carroll&#10026;  -
snapd                2.59.1           18933  latest/stable  canonical&#10003;      snapd

```

How can I solve this?

Best Regards,
Pau

---

### Post by ajgreeny on 2023-05-02
Probably a permissions or ownership problem, but it's impossible to know with the information you have given us.

Tell us more and show the output of command ```
sudo fdisk -l
``` using code-tags please.

---

### Post by pautorras on 2023-05-02
Hi,

See attached the results of fdisk -l

```

Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 9,56 MiB, 10027008 bytes, 19584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 9,56 MiB, 10027008 bytes, 19584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 116,79 MiB, 122458112 bytes, 239176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 116,76 MiB, 122433536 bytes, 239128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 63,29 MiB, 66359296 bytes, 129608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 63,32 MiB, 66392064 bytes, 129672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 72,99 MiB, 76537856 bytes, 149488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 953,87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: SAMSUNG MZAL41T0HBLB-00BL2              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: CB5965D0-A544-49BD-97E6-C9744D69A88C

Dispositiu       Start      Final    Sectors   Size Tipus
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953,4G Linux filesystem


Disk /dev/nvme1n1: 931,51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: CT1000P5PSSD8                           
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 349,69 MiB, 366673920 bytes, 716160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 349,69 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 460,57 MiB, 482947072 bytes, 943256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 460,56 MiB, 482930688 bytes, 943224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 91,69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 51,54 MiB, 54046720 bytes, 105560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 49,84 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 53,24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 72,99 MiB, 76537856 bytes, 149488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by oldfred on 2023-05-02
We do not need all the loops, those are just your snap apps.

You show no partition(s) on your second NVMe drive. Be sure to use gpt, gparted often defaults to MBR.
You need to create a partition, and format it. If only Linux use ext4. You can use gparted from live installer or from your install, since second drive.
You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

And then give yourself owership & permissions.
And if permanently installed & you want it auto mounted on reboot, best to add to fstab.
I also prefer to label partitions when I create them, so any partitions that I do not mount with fstab get mounted with the label which is a lot more useful than the auto mount by  UUID.

Some suggest using Disks (gnome-disks), but it does not default to best mount parameters.

Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
ext4 example - TheFu
[https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting.

---

### Post by pautorras on 2023-05-03
Hi,

Before starting making partition changes, I've a question.
Why Google Chrome don't give me any problems with the second internal drive about permissions,..., and with Firefox I get those problems?

It's really a partition problem?

Thanks in advance.

Pau

---

### Post by oldfred on 2023-05-03
Know nothing about Chrome.
Sounds like a Chome issue.

---

### Post by pautorras on 2023-05-05
Hi folks,


Problem solved.
Finally I've freaked out with firefox and I have uninstalled it.
I've installed Brave browser instead, and it's working fine.


Only one problem with brave browser, fixed with that command:
```

dconf write /org/gnome/desktop/sound/input-feedback-sounds false

```

Thanks.

---

