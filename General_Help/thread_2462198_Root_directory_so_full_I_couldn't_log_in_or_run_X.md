---
title: "Root directory so full I couldn't log in or run X"
date: 2021-05-15
forum: General Help
---

### Post by goemonburo on 2021-05-15
Rebooted my system to find that while I could get to the login X window, Xorg gave an error saying there wasn't enough memory when I tried to log in.  And the only way I was able to get in was to use Ctl-Alt-F4 and log in at the terminal, then run a bunch of diagnostics that showed among other things my log files were 4GB.  I eventually used

```
journalctl --rotate --vacuum-size=500M
```

to shrink them and now can log in, (whew!) but "df" shows that I'm still at 100% of my root directory, along with a bunch of /snap partitions.  I think it's something like an 8GB partition which should be ample (huge!) for most needs.  What am I missing and is there a way to clean this further and prevent it from happening again?

```
Filesystem      1K-blocks       Used  Available Use% Mounted on
udev             20339412          0   20339412   0% /dev
tmpfs             4079884       1984    4077900   1% /run
/dev/sda7       741215896  699622080    3872372 100% /
tmpfs            20399408       1368   20398040   1% /dev/shm
tmpfs                5120          4       5116   1% /run/lock
tmpfs            20399408          0   20399408   0% /sys/fs/cgroup
/dev/loop3          56832      56832          0 100% /snap/core18/1988
/dev/loop7            256        256          0 100% /snap/gtk2-common-themes/13
/dev/loop1         196352     196352          0 100% /snap/glimpse-editor/191
/dev/loop2          56832      56832          0 100% /snap/core18/1997
/dev/loop4         101376     101376          0 100% /snap/core/11081
/dev/loop0         101632     101632          0 100% /snap/core/10958
/dev/loop8          32896      32896          0 100% /snap/snapd/11841
/dev/loop11        188032     188032          0 100% /snap/vidcutter/14
/dev/loop13         33152      33152          0 100% /snap/snapd/11588
/dev/loop5         166784     166784          0 100% /snap/gnome-3-28-1804/145
/dev/loop10        183936     183936          0 100% /snap/spotify/46
/dev/loop12        183808     183808          0 100% /snap/spotify/45
/dev/loop9          66432      66432          0 100% /snap/gtk-common-themes/1514
/dev/loop6         178304     178304          0 100% /snap/glimpse-editor/194
/dev/loop14         66688      66688          0 100% /snap/gtk-common-themes/1515
/dev/sdb1      3844660232  833962368 2815330648  23% /home
/dev/sda1          661504      73388     588116  12% /boot/efi
```

---

### Post by CharlesA on 2021-05-15
Run this to narrow down which folder is sucking all the space.

```
sudo du -h --exclude /home --exclude /dev --exclude /sys --exclude /proc --max-depth=1 /
```

It'll give you a list like this:

```

633M    /lib
10M     /bin
16K     /lost+found
40K     /tmp
1.2G    /usr
78M     /boot
4.0K    /lib64
8.0K    /media
4.0K    /opt
56K     /root
4.0K    /srv
420M    /var
7.5M    /sbin
4.2M    /etc
4.0K    /mnt
4.2M    /run
2.3G    /

```

---

### Post by deadflowr on 2021-05-15
snaps take no space in /snap on disk.
All snaps disk space is taken in /var/lib/snapd/snaps.
/snap is a loop mount, so even though it will show as a certain amount of space being used, none is on disk.

Edit: you can cut out the snap listings from df with
```
df -Th -x squashfs

```
Which will also give you a more human readable output.

---

### Post by Impavidus on 2021-05-16
8GB is rather small for a root partition these days. It's better to make it at least 25GB. However, your output shows it's over 700GB, which should be enough. Start digging and look for the offending files/directories.

And those 4GB of logs were not the problem.

---

