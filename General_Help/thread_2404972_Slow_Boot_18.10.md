---
title: "Slow Boot 18.10"
date: 2018-10-30
forum: General Help
---

### Post by Joe Jameson on 2018-10-30
G'day,
            I know this bug is widespread as both my Lenlovo ideapad 110 and my son't Gateway take up to 2 mins to boot, I've searched and found the possible cause is the incorrect swap is found, so could someone please
point me to a Tutorial to correct the problem, I've been waiting for a fix from Ubuntu but so far no go,
regards Joe.

---

### Post by nlee2 on 2018-10-30
Care to provide more detail on "this bug"?
Please provide the link to article on possible cause.

What is the output of

systemd-analyze blame

---

### Post by Joe Jameson on 2018-10-30
G'day nlee2, as asked this is one link,  [https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
and terminal output:  systemd-analyze blame
         51.982s apt-daily.service
         28.220s plymouth-quit-wait.service
         14.557s dev-sda4.device
         10.963s dev-loop12.device
         10.885s dev-loop11.device
         10.794s dev-loop13.device
         10.791s dev-loop10.device
         10.691s dev-loop15.device
          9.951s udisks2.service
          9.449s dev-loop9.device
          9.231s networkd-dispatcher.service
          8.361s ModemManager.service
          8.034s dev-loop8.device
          7.903s dev-loop14.device
          7.207s dev-loop0.device
          7.204s dev-loop7.device
          7.075s dev-loop1.device
          7.046s dev-loop5.device
          7.029s dev-loop4.device
          7.010s accounts-daemon.service
          6.972s dev-loop3.device
          6.705s dev-loop6.device
          6.075s dev-loop2.device
lines 1-23

---

### Post by nlee2 on 2018-10-31
The problem that I see is all versions of snaps are mounted. You could remove all old versions of install snaps and any unused snaps to speed up boot time.

What is the output of

df -Th

---

### Post by Joe Jameson on 2018-10-31
Here tis: $ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.4G     0  3.4G   0% /dev
tmpfs          tmpfs     688M  1.7M  686M   1% /run
/dev/sda4      ext4      241G   11G  218G   5% /
tmpfs          tmpfs     3.4G  9.1M  3.4G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.4G     0  3.4G   0% /sys/fs/cgroup
/dev/loop0     squashfs   88M   88M     0 100% /snap/core/5662
/dev/loop1     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop2     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop3     squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop14    squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop4     squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop5     squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop6     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop8     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop9     squashfs   88M   88M     0 100% /snap/core/5548
/dev/loop12    squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop11    squashfs   13M   13M     0 100% /snap/gnome-characters/124
/dev/loop7     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop15    squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop13    squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/238
/dev/loop10    squashfs   43M   43M     0 100% /snap/gtk-common-themes/701
/dev/sda1      vfat      511M  7.3M  504M   2% /boot/efi
tmpfs          tmpfs     688M   28K  688M   1% /run/user/1000

Could you please etll me an instruction to for me to compare my actual swap partition with the one my computer thinks it is?

---

### Post by nlee2 on 2018-10-31
cat /etc/fstab
blkid

---

### Post by Joe Jameson on 2018-10-31
G'day nlee2 and thanks for your help, i followed your instructions and found something interesting, check this out:$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=d7ef9829-b9d8-41be-97e2-9ce072ccef2b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=0176-BD87  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

$ sudo blkid
[sudo] password for joe: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="0176-BD87" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="61d94f0f-921f-46ee-9b95-0574e77ec004"
/dev/sda2: UUID="e2f8f1e4-2f3b-45ea-a505-2804b1d9b0d0" TYPE="ext4" PARTUUID="7de7d171-b864-41d1-8d4a-60736de0687c"
/dev/sda3: UUID="57ea9736-9eac-4b6c-9298-a7d56aa347dd" TYPE="swap" PARTUUID="934d6e05-962c-40b3-be70-5e81f3c703f9"
/dev/sda4: UUID="d7ef9829-b9d8-41be-97e2-9ce072ccef2b" TYPE="ext4" PARTUUID="6dd75668-3801-4788-9ee0-9d6eb3f6848f"
/dev/sda5: UUID="6457db25-93be-4927-be43-d63e66966e34" TYPE="ext4" PARTUUID="82313ae4-911a-4837-a325-b92eb2a1ed39"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"


sda3 is my swap 18gig partition, I wonder why it is not in fstab, Joe.

---

### Post by nlee2 on 2018-10-31
Your swap is /swapfile. Your root partition including /swapfile is only 11GB used (5%).

I do not see that it will make any difference but to switch swap to /dev/sda3 

swapoff /swapfile
swapon /dev/sda3
reboot

You can shave one minute off your boot time just by deleting old versions of snaps.

---

### Post by Joe Jameson on 2018-10-31
I set sda3 as swapon and ran this script, booted in 75 seconds, the boot seems to freeze for ten seconds with a ubuntu logo with dots underneath, not tooo bad but still pretty slow for a modern quad core 8 gig jigger, I can live with it though.
Script: up vote

down vote
Here's a short script which will remove all old versions of snaps. This will only keep the current active version, which should recover you some disk space.

#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
 Joe.

---

### Post by Joe Jameson on 2018-11-01
I set sda3 as swapon and ran this script, booted in 75 seconds, the boot seems to freeze for ten seconds with a ubuntu logo with dots underneath, not tooo bad but still pretty slow for a modern quad core 8 gig jigger, I can live with it though.
Script: up vote

down vote
Here's a short script which will remove all old versions of snaps. This will only keep the current active version, which should recover you some disk space.

#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
 Joe.

---

### Post by Joe Jameson on 2018-11-01
After script :
$ systemd-analyze blame
         27.262s plymouth-quit-wait.service
         11.047s dev-sda4.device
         10.081s udisks2.service
          9.065s networkd-dispatcher.service
          6.155s dev-loop9.device
          6.105s dev-loop11.device
          6.007s ModemManager.service
          5.925s dev-loop10.device
          5.924s dev-loop15.device
          5.865s dev-loop14.device
          5.576s dev-loop13.device
          5.553s NetworkManager.service
          5.548s dev-loop8.device
          5.500s dev-loop12.device
          5.415s accounts-daemon.service
          5.095s snapd.service
          4.698s wpa_supplicant.service
          4.516s dev-loop7.device
          4.511s networking.service
          4.414s dev-loop5.device
          4.414s dev-loop6.device
          4.318s dev-loop0.device

---

