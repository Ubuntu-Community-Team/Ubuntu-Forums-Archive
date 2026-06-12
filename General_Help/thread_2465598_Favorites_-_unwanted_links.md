---
title: "Favorites - unwanted links"
date: 2021-08-06
forum: General Help
---

### Post by UBUminJ on 2021-08-06
In the favorites bar, I just found two new ones which I didn't added.
A link to "filesystem root" and a link to "efi".

Do you have any idea how this could have happened - and how can I get rid of these links?

The only thing which I recently did was the installation of "world clocks".

---

### Post by UBUminJ on 2021-08-06
In the Favorites section of Ubuntu 2004, I found links to the mounted "Filesystem root". I didn't mount these. Unmount doesn't work.
How can I achieve this?

---

### Post by QIII on 2021-08-06
By shutting down your machine. When your machine is running the OS, / is in use by it.

Why do you want to unmount it?


Moved to General Help.

---

### Post by UBUminJ on 2021-08-06
The links in the Favorites as well as the mounts in Nautilus have never been there before. So, I am wondering if something is wrong.
"efi" is also mounted

---

### Post by QIII on 2021-08-06
Are you looking at "Other Locations"?

---

### Post by UBUminJ on 2021-08-06
I show you a screenshot - on the left you see the two grey disks - appeared probably yesterday.
And in Nautilus the corresponding disks.

[ATTACH=CONFIG]288939[/ATTACH]

---

### Post by UBUminJ on 2021-08-06
What I have done recently to the system was just installing Gnome-clocks (installed two/three days ago, uninstalled meanwhile because it didn't work properly) and before, installation of Google Chrome (but that is already a few days before).

---

### Post by &amp;KyT$0P# on 2021-08-06
So you just want these mounts to not show up like that?

Can you please post the outputs from running these two commands in Terminal? -
```
findmnt
cat /etc/fstab
```

---

### Post by UBUminJ on 2021-08-07
If something is different from the usual, I simply do not know enough to look into the problems by myself.
Depend on outside help. Thank you.

findmnt

```
TARGET                                SOURCE           FSTYPE  OPTIONS
/                                     /dev/sda5        ext4    rw,relatime,error
&#9500;&#9472;/sys                                sysfs            sysfs   rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/kernel/security              securityfs       securit rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/fs/cgroup                    tmpfs            tmpfs   ro,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/unified          cgroup2          cgroup2 rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/systemd          cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/freezer          cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpu,cpuacct      cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/rdma             cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/hugetlb          cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/devices          cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/net_cls,net_prio cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpuset           cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/perf_event       cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/blkio            cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/memory           cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9474; &#9492;&#9472;/sys/fs/cgroup/pids             cgroup           cgroup  rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/fs/pstore                    pstore           pstore  rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/fs/bpf                       none             bpf     rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/kernel/tracing               tracefs          tracefs rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/kernel/debug                 debugfs          debugfs rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/sys/fs/fuse/connections          fusectl          fusectl rw,nosuid,nodev,n
&#9474; &#9492;&#9472;/sys/kernel/config                configfs         configf rw,nosuid,nodev,n
&#9500;&#9472;/proc                               proc             proc    rw,nosuid,nodev,n
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc          systemd-1        autofs  rw,relatime,fd=28
&#9500;&#9472;/dev                                udev             devtmpf rw,nosuid,noexec,
&#9474; &#9500;&#9472;/dev/pts                          devpts           devpts  rw,nosuid,noexec,
&#9474; &#9500;&#9472;/dev/shm                          tmpfs            tmpfs   rw,nosuid,nodev,i
&#9474; &#9500;&#9472;/dev/hugepages                    hugetlbfs        hugetlb rw,relatime,pages
&#9474; &#9492;&#9472;/dev/mqueue                       mqueue           mqueue  rw,nosuid,nodev,n
&#9500;&#9472;/run                                tmpfs            tmpfs   rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/run/lock                         tmpfs            tmpfs   rw,nosuid,nodev,n
&#9474; &#9500;&#9472;/run/user/1000                    tmpfs            tmpfs   rw,nosuid,nodev,r
&#9474; &#9474; &#9500;&#9472;/run/user/1000/gvfs             gvfsd-fuse       fuse.gv rw,nosuid,nodev,r
&#9474; &#9474; &#9492;&#9472;/run/user/1000/doc              /dev/fuse        fuse    rw,nosuid,nodev,r
&#9474; &#9492;&#9472;/run/snapd/ns                     tmpfs[/snapd/ns] tmpfs   rw,nosuid,nodev,n
&#9474;   &#9492;&#9472;/run/snapd/ns/snap-store.mnt    nsfs[mnt:[4026532242]]
&#9474;                                                      nsfs    rw
&#9500;&#9472;/snap/core18/2074                   /dev/loop1       squashf ro,nodev,relatime
&#9500;&#9472;/snap/core18/2066                   /dev/loop0       squashf ro,nodev,relatime
&#9500;&#9472;/snap/core20/1026                   /dev/loop2       squashf ro,nodev,relatime
&#9500;&#9472;/snap/chromium/1685                 /dev/loop3       squashf ro,nodev,relatime
&#9500;&#9472;/snap/chromium/1691                 /dev/loop5       squashf ro,nodev,relatime
&#9500;&#9472;/snap/core20/1081                   /dev/loop4       squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-28-1804/161           /dev/loop6       squashf ro,nodev,relatime
&#9500;&#9472;/snap/gimp/372                      /dev/loop7       squashf ro,nodev,relatime
&#9500;&#9472;/snap/gimp/367                      /dev/loop8       squashf ro,nodev,relatime
&#9500;&#9472;/snap/gtk-common-themes/1515        /dev/loop9       squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-28-1804/145           /dev/loop10      squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-34-1804/66            /dev/loop11      squashf ro,nodev,relatime
&#9500;&#9472;/snap/snapd/12704                   /dev/loop12      squashf ro,nodev,relatime
&#9500;&#9472;/snap/snapd/12398                   /dev/loop13      squashf ro,nodev,relatime
&#9500;&#9472;/snap/gtk-common-themes/1514        /dev/loop14      squashf ro,nodev,relatime
&#9500;&#9472;/snap/snap-store/547                /dev/loop15      squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-34-1804/72            /dev/loop16      squashf ro,nodev,relatime
&#9500;&#9472;/snap/snap-store/542                /dev/loop17      squashf ro,nodev,relatime
&#9500;&#9472;/snap/kde-frameworks-5-core18/32    /dev/loop18      squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-38-2004/39            /dev/loop19      squashf ro,nodev,relatime
&#9492;&#9472;/boot/efi                           /dev/sda1        vfat    rw,relatime,fmask

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=de31bdc3-530a-406f-bd68-8f66b9e178e0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=881B-1069  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by UBUminJ on 2021-08-07
I don't know why it happened but after several starts and shut-downs, the links and the entries have all vanished.
What I did today was the deinstallation of gnome clocks.

Just as an uneducated guess, this was the "culprit".

Thank you for your answers anyway.

---

### Post by ActionParsnip on 2021-08-07
The favourites bar in what application please? Firefox?

---

### Post by ajgreeny on 2021-08-07
I suspect the favourites/bookmarks are in your file manager but please tell us a lot more detail of your system and the OS that you're using, particularly the DE or we are just guessing.

---

### Post by UBUminJ on 2021-08-07
And they are back.

---

### Post by coffeecat on 2021-08-07
@UBUminL, I've merged your two recent threads. Although with different titles, they are about the same problem. Please do not post duplicate threads - it causes confusion and dilutes community effort. There has already been confusion with these two threads with people responding in one thread unaware of what has been said in the other.

---

### Post by deadflowr on 2021-08-07
I'm not sure what's going on with the File Manager showing those, but you should be able to disable the ones in the dock using dconf or gsettings like
```
gsettings get org.gnome.shell.extensions.dash-to-dock show-mounts
```
if true change to false.
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false
```

---

### Post by UBUminJ on 2021-08-07
@ActionParsnip 
I was talking about the favorites bar in Ubuntu 20.04.

@deadflowr
Thank you, your code removed the links. But the mounts show up in Nautilus which they didn't until a few days before.
Just found out that there seem to be more problems. A typically used USB memory inserted doesn't mount in Nautilus.

---

### Post by UBUminJ on 2021-08-07
I just mounted the USB memory. This mount point also shows up in Nautilus - and remains after removing the memory stick.
Could it be a corrupted Nautilus? What do you think?

---

### Post by &amp;KyT$0P# on 2021-08-08
I'm not noticing any problems in the terminal outputs you posted earlier.

Maybe check into the status of GVFS?  I'm not sure exactly how to check that, but I'd start with the following Terminal commands -
```
dpkg-query -W | grep -i gvfs
systemctl --user list-units '*gvfs*'
ps aux | grep -i gvfs
```

Maybe there would be something relevant in [FONT=Courier New]/var/log/syslog[/FONT] especially around the time you eject+unplug USB stick and the mount entry remains?

---

