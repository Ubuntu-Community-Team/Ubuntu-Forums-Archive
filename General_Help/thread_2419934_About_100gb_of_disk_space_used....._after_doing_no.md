---
title: "About 100gb of disk space used..... after doing nothing!"
date: 2019-05-27
forum: General Help
---

### Post by mrproyaku on 2019-05-27
My HDD, for seemingly no reason, is 5.9mb out of 177.3gb full! Just yesterday I had more than half the HDD free. The only recent downloads/installs I have made are from Steam, and the game I installed was certainly not even near a single GB in space. What's going on?

---

### Post by Rubi1200 on 2019-05-27
Hi,

can we see the output of the following please:

```
df -T -h
```

Thanks.

---

### Post by mrproyaku on 2019-05-27
```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     390M  6.5M  384M   2% /run
/dev/sda7      ext4      166G   71G   87G  45% /
tmpfs          tmpfs     2.0G   33M  1.9G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop1     squashfs   54M   54M     0 100% /snap/core18/970
/dev/loop2     squashfs  295M  295M     0 100% /snap/pycharm-community/121
/dev/loop3     squashfs   66M   66M     0 100% /snap/discord/92
/dev/loop4     squashfs  519M  519M     0 100% /snap/libreoffice/119
/dev/loop6     squashfs   35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop5     squashfs   66M   66M     0 100% /snap/discord/91
/dev/loop7     squashfs   89M   89M     0 100% /snap/core/6964
/dev/loop8     squashfs  141M  141M     0 100% /snap/sftpclient/79
/dev/loop9     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/78
/dev/loop10    squashfs  298M  298M     0 100% /snap/pycharm-community/128
/dev/loop11    squashfs  519M  519M     0 100% /snap/libreoffice/120
/dev/loop12    squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/82
/dev/loop13    squashfs   90M   90M     0 100% /snap/core/6818
/dev/loop14    squashfs   36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop15    squashfs   54M   54M     0 100% /snap/core18/782
/dev/loop0     squashfs   66M   66M     0 100% /snap/discord/93
/dev/loop16    squashfs  141M  141M     0 100% /snap/sftpclient/78
/dev/loop17    squashfs   45M   45M     0 100% /snap/openspades/10
/dev/loop18    squashfs   54M   54M     0 100% /snap/core18/941
/dev/loop19    squashfs  296M  296M     0 100% /snap/pycharm-community/123
/dev/loop20    squashfs   90M   90M     0 100% /snap/core/6673
/dev/loop21    squashfs  141M  141M     0 100% /snap/sftpclient/74
/dev/sda2      vfat       96M   29M   68M  30% /boot/efi
tmpfs          tmpfs     390M   84K  390M   1% /run/user/1000


```

I just checked my HDD again, it seems to be back at normal, for now... Not sure what was happening there. I had emptied my trash bin, I know after that it had freed about 19gb, surprisingly. But the other ~80gb??? That came back just now, not sure why or where it was when I made this post. I highly doubt it was all stuffed in the bin and that was the problem. To have 80+gb in there is unlikely to me, but if that was the cause I feel kinda silly, haha.

---

### Post by Rubi1200 on 2019-05-27
Looks basically normal to me.

You could, if you want, remove older versions of snaps keeping only the most current or recent one.
[https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

Bear in mind that it won't free up that much space (in most cases).

If you need more help, feel free to ask.

---

### Post by deadflowr on 2019-05-27
For what it's worth, you can cut out those snaps from the dh output with *-x squashfs* like
```
df -h -x squashfs
```
It's won't affect or change the disk space usage output since all snap disk space usage are already outputted in the main file systems outputs.

---

