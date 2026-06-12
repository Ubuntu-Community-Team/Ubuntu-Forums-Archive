---
title: "/dev/loop0, /dev/loop1 and so on when on the terminal I type the command df -h"
date: 2019-04-25
forum: General Help
---

### Post by albertxe on 2019-04-25
Hi:
I'm pretty new in Ubuntu. I'm from the Basque Country and I need your help.

I'm using Ubuntu 18.04. Today, when I was going to defragment my hard disk and I typed df -h in the terminal I had the following:

```
[COLOR=#ff0000]Fitxategi-sistema Tamai  Erab Libre Erab% Non muntatua[/COLOR]
udev               1,9G     0  1,9G    0% /dev
tmpfs              387M  1,7M  385M    1% /run
/dev/sda5          454G  382G   53G   88% /
tmpfs              1,9G     0  1,9G    0% /dev/shm
tmpfs              5,0M  4,0K  5,0M    1% /run/lock
tmpfs              1,9G     0  1,9G    0% /sys/fs/cgroup
/dev/loop1         141M  141M     0  100% /snap/gnome-3-26-1604/74
/dev/loop3         141M  141M     0  100% /snap/gnome-3-26-1604/78
/dev/loop4          91M   91M     0  100% /snap/core/6405
/dev/loop5         1,0M  1,0M     0  100% /snap/gnome-logs/61
/dev/loop8         152M  152M     0  100% /snap/gnome-3-28-1804/31
/dev/loop9         1,0M  1,0M     0  100% /snap/gnome-logs/57
/dev/loop10        4,2M  4,2M     0  100% /snap/gnome-calculator/406
/dev/loop0          15M   15M     0  100% /snap/gnome-characters/254
/dev/loop2         152M  152M     0  100% /snap/gnome-3-28-1804/36
/dev/loop6         4,2M  4,2M     0  100% /snap/gnome-calculator/352
/dev/loop7          13M   13M     0  100% /snap/gnome-characters/139
/dev/loop13         36M   36M     0  100% /snap/gtk-common-themes/1198
/dev/loop12         35M   35M     0  100% /snap/gtk-common-themes/1122
/dev/loop15         36M   36M     0  100% /snap/gtk-common-themes/1269
/dev/loop16         54M   54M     0  100% /snap/core18/941
/dev/loop18        141M  141M     0  100% /snap/gnome-3-26-1604/82
/dev/loop17         15M   15M     0  100% /snap/gnome-characters/206
/dev/loop11        203M  203M     0  100% /snap/vlc/770
/dev/loop19         54M   54M     0  100% /snap/core18/782
/dev/loop14        144M  144M     0  100% /snap/gnome-3-28-1804/23
/dev/loop20         89M   89M     0  100% /snap/mcomix-tabetai/7
/dev/loop21         15M   15M     0  100% /snap/gnome-logs/45
/dev/loop23        3,8M  3,8M     0  100% /snap/gnome-system-monitor/70
/dev/loop25         92M   92M     0  100% /snap/core/6531
/dev/loop26        196M  196M     0  100% /snap/vlc/555
/dev/loop28        3,8M  3,8M     0  100% /snap/gnome-system-monitor/57
/dev/loop22        2,3M  2,3M     0  100% /snap/gnome-calculator/260
/dev/loop27        3,8M  3,8M     0  100% /snap/gnome-system-monitor/77
/dev/loop24         90M   90M     0  100% /snap/core/6673
/dev/loop29        203M  203M     0  100% /snap/vlc/768
tmpfs              387M   40K  387M    1% /run/user/1000
```

The words in red are in my language (Basque) but I think that you can understand them

What've happened with may hard disk? Could you help me?

Thank you

---

### Post by again? on 2019-04-25
These are virtual mounts for snap packages.
[https://en.wikipedia.org/wiki/Snappy_(package_manager)](https://en.wikipedia.org/wiki/Snappy_(package_manager))
Ubuntu 18.04 installs some core packages as snaps.

---

### Post by Rubi1200 on 2019-04-25
Why do you think you need to defragment the hard drive?

---

