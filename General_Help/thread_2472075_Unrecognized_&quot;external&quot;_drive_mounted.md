---
title: "Unrecognized &quot;external&quot; drive mounted"
date: 2022-02-16
forum: General Help
---

### Post by Mike_Schmidt on 2022-02-16
I'm on Ubuntu 20.04.04.3 LTS and I see a new drive mounted as though it's a usb drive or cd, but I don't have anything plugged in that would have storage, and there's no optical drive on my machine. Its contents look like a boot drive, but my machine's boot drive is listed separately (below). I am nearly certain I haven't mounted any iso images and I'm not actively running any virtual machine software. Anybody know what's causing this or what it's doing? It's the very last mount listed below (/dev/loop11).

```
mike@cardano:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
udev                               16G     0   16G   0% /dev
tmpfs                             3.2G  2.5M  3.2G   1% /run
/dev/nvme0n1p2                    938G  815G   76G  92% /
tmpfs                              16G  332M   16G   3% /dev/shm
tmpfs                             5.0M  4.0K  5.0M   1% /run/lock
tmpfs                              16G     0   16G   0% /sys/fs/cgroup
/dev/loop0                        9.2M  9.2M     0 100% /snap/canonical-livepatch/126
/dev/loop1                        128K  128K     0 100% /snap/bare/5
/dev/loop2                        219M  219M     0 100% /snap/gnome-3-34-1804/77
/dev/loop4                        9.2M  9.2M     0 100% /snap/canonical-livepatch/119
/dev/loop5                        133M  133M     0 100% /snap/chromium/1895
/dev/loop6                        193M  193M     0 100% /snap/signal-desktop/379
/dev/loop7                         62M   62M     0 100% /snap/core20/1328
/dev/loop8                        296M  296M     0 100% /snap/vlc/2288
/dev/loop9                        163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop10                        55M   55M     0 100% /snap/snap-store/558
/dev/loop12                        62M   62M     0 100% /snap/core20/1270
/dev/nvme0n1p1                    511M   48M  464M  10% /boot/efi
/dev/loop14                       216M  216M     0 100% /snap/code/87
/dev/loop15                       213M  213M     0 100% /snap/code/88
/dev/loop16                        51M   51M     0 100% /snap/snap-store/547
/dev/loop17                       219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop18                        66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop20                        56M   56M     0 100% /snap/core18/2253
/dev/loop21                       187M  187M     0 100% /snap/signal-desktop/383
/dev/loop22                       165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop23                       249M  249M     0 100% /snap/gnome-3-38-2004/99
/dev/loop24                       135M  135M     0 100% /snap/chromium/1899
/dev/loop25                       296M  296M     0 100% /snap/vlc/2344
/dev/loop26                       248M  248M     0 100% /snap/gnome-3-38-2004/87
/dev/loop27                        56M   56M     0 100% /snap/core18/2284
/dev/loop28                        66M   66M     0 100% /snap/gtk-common-themes/1515
tmpfs                             3.2G   84K  3.2G   1% /run/user/1000
/dev/loop29                       111M  111M     0 100% /snap/core/12725
/dev/loop30                        44M   44M     0 100% /snap/snapd/14978
jjm2:/data/BI/human/rawdata        54T   51T  228G 100% /mnt/rawdata
jjm2:/data/BI/human/derivatives    54T   51T  228G 100% /mnt/derivatives
/dev/loop11                       111M  111M     0 100% /media/mike/disk

```

```
mike@cardano:~$ ls -l /media/mike/disk/
total 0
drwxr-xr-x  2 root root 1975 Jan  6 21:21 bin
drwxr-xr-x  6 root root  129 Jan  6 21:21 boot
drwxr-xr-x  4 root root 1160 Jan  6 21:21 dev
drwxr-xr-x 79 root root 2367 Jan  6 21:21 etc
drwxr-xr-x  2 root root    3 Apr 12  2016 home
drwxr-xr-x 20 root root  418 Jan  6 21:21 lib
drwxr-xr-x  2 root root   43 Jan  6 21:21 lib64
drwxr-xr-x  2 root root    3 Jan  6 21:16 media
drwxr-xr-x  3 root root   45 Jan  6 21:21 meta
drwxr-xr-x  2 root root    3 Jan  6 21:16 mnt
drwxr-xr-x  2 root root    3 Jan  6 21:16 opt
drwxr-xr-x  2 root root    3 Apr 12  2016 proc
drwx------  2 root root   46 Jan  6 21:21 root
drwxr-xr-x 11 root root  187 Jan  6 21:21 run
drwxr-xr-x  2 root root 2349 Jan  6 21:21 sbin
drwxr-xr-x  2 root root   58 Jan  6 21:21 snap
drwxr-xr-x  2 root root    3 Jan  6 21:16 srv
drwxr-xr-x  2 root root    3 Feb  5  2016 sys
drwxrwxrwt  2 root root    3 Jan  6 21:19 tmp
drwxr-xr-x 11 root root  163 Jan  6 21:21 usr
drwxr-xr-x 12 root root  160 Jan  6 21:21 var
drwxr-xr-x  2 root root    3 Jan  6 21:19 writable

```

```

mike@cardano:~$ sudo parted -l
Model: KXG50ZNV1T02 NVMe TOSHIBA 1024GB (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1024GB  1024GB  ext4

```

It shows up in the graphical Disks app as "116 MB Loop Device" from "/var/lib/snapd/snaps/core_12603.snap (deleted)". The (deleted) description doesn't seem accurate as I can still explore the directory structure and read files from bash or nautilus. It appears in nautilus with an eject button as though it's removable storage.

Obviously, there are a bunch of snaps running, but this one behaves differently and I don't remember ever seeing it before. I can't remember having installed any new software lately either.

Thanks!

---

### Post by TheFu on 2022-02-16
All 'loop' devices are snaps.  Send your thanks to Canonical for this aspect of their snap package implementation.
Of you don't want to see that, use these aliases:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblk='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
Those show only real storage devices.

---

### Post by Mike_Schmidt on 2022-02-16
Thanks @TheFu. Perhaps a better question, that I should have asked, is "Should I be concerned this loop device or snap has mounted at /media/mike/disk/ rather than /snap/ and shows up as an external drive?" It seems odd compared to other snap behavior, which makes me wonder if perhaps it didn't come from standard software sources.

---

### Post by MAFoElffen on 2022-02-17
You have my curiosity! LOL

It would be worth it to investigate
```

awk '{print $0}' /media/mike/disk//etc/lsb-release

```

---

### Post by Mike_Schmidt on 2022-02-17
Thank you @MAFoElffen. I left my computer running overnight and came back to a black screen, but a functioning mouse cursor. :( Happens occasionally and probably unrelated. But I am hesitant to reboot until figuring this out. Using Ctrl+Alt+F4 for a console got me this:

```

mike@cardano:~$ awk '{print $0}' /media/mike/disk//etc/lsb-release
DISTRIB_ID="Ubuntu Core"
DISTRIB_RELEASE=16
DISTRIB_DESCRIPTION="Ubuntu Core 16"

```

---

### Post by grahammechanical on 2022-02-17
You installed the Signal Desktop messaging app. It is in the Ubuntu  software store as a snap packaged app. It is my guess that it is Signal  that has produced this loop device that seems to be a drive.

I  installed an Android emulator called Anbox as a snap and it presents 326  MB loop device as a drive. According to Disks it is read only squashfs.

That  this should be done this way I do not know. I agree with the point made  above that it is function of the snap package system and the demands of  the developer's application. It could be that doing things this way is  more secure than doing things another way.

Regards

---

### Post by Mike_Schmidt on 2022-02-17
Thank you @grahammechanical. You are correct that I've installed the signal app. But I'm not convinced that's related to my question. Signal shows up twice, interestingly, as /snap/signal-desktop/379/ and /snap/signal-desktop/383/. So I thought from your comment, that maybe this new removable drive is a third instance of signal? But signal has been installed for well over a year without ever creating a removable drive. I haven't used it from ubuntu in months, only on my phone, so I deleted it from my laptop just now.

```
sudo snap remove signal-desktop
```

Both signal-desktop snaps are now gone, but the /media/mike/disk remains.

---

### Post by Mike_Schmidt on 2022-02-17
I have done a little more digging. It seemed perhaps coincidental that the /snap/core/12725/ and this new external drive are the same size, so I compared them.

```

mike@cardano:~$ 2>/dev/null ls -1 --recursive /media/mike/disk/ | wc -l
15737
mike@cardano:~$ 2>/dev/null ls -1 --recursive /snap/core/12725/ | wc -l
15737
2>/dev/null diff -r --no-dereference /snap/core/12725/ /media/mike/disk/ | tee -a ~/snap_diffs.txt

```

The differences seem minor. There are only 6 text files that differ, the most common difference being "2.54.2" vs "2.54.3" versions. There are 23 binary files that differ, but no evidence either of these structures has a different set of files compared to the other.

```

diff -r --no-dereference /snap/core/12725/etc/apparmor.d/usr.lib.snapd.snap-confine.real /media/mike/disk/etc/apparmor.d/usr.lib.snapd.snap-confine.real
48,58d47
<     # This rule is needed when executing from a "base: core" devmode snap on
<     # UC18 and newer where the /usr/lib/snapd/snap-confine inside the
<     # "base: core" mount namespace always comes from the snapd snap, and thus
<     # we will execute snap-confine via this path, and thus need to be able to
<     # read this path when executing. It's also necessary on classic where both
<     # the snapd and the core snap are installed at the same time.
<     # TODO: remove this rule when we stop supporting executing other snaps from
<     # inside devmode snaps, ideally even in the short term we would only include
<     # this rule on core only, and specifically uc18 and newer where we need it
<     #@VERBATIM_LIBEXECDIR_SNAP_CONFINE@ mr,
<
414c403
<     @{HOME}/.Private/** mrwlk,
---
>     @{HOME}/.Private/** mrixwlk,
417c406
<     @{HOMEDIRS}/.ecryptfs/*/.Private/** mrwlk,
---
>     @{HOMEDIRS}/.ecryptfs/*/.Private/** mrixwlk,
Binary files /snap/core/12725/lib/systemd/system-generators/snapd-generator and /media/mike/disk/lib/systemd/system-generators/snapd-generator differ
Binary files /snap/core/12725/lib/udev/snappy-app-dev and /media/mike/disk/lib/udev/snappy-app-dev differ
diff -r --no-dereference /snap/core/12725/meta/snap.yaml /media/mike/disk/meta/snap.yaml
2c2
< version: 16-2.54.3
---
> version: 16-2.54.2
diff -r --no-dereference /snap/core/12725/snap/manifest.yaml /media/mike/disk/snap/manifest.yaml
233c233
<     - snapd=2.54.3
---
>     - snapd=2.54.2
485c485
<     - snapd=2.54.3
---
>     - snapd=2.54.2
870c870
<     - snapd=2.54.3
---
>     - snapd=2.54.2
1284c1284
<     - snapd=2.54.3
---
>     - snapd=2.54.2
1694c1694
<     - snapd=2.54.3
---
>     - snapd=2.54.2
2104c2104
<     - snapd=2.54.3
---
>     - snapd=2.54.2
Binary files /snap/core/12725/usr/bin/snap and /media/mike/disk/usr/bin/snap differ
Binary files /snap/core/12725/usr/bin/snapfuse and /media/mike/disk/usr/bin/snapfuse differ
diff -r --no-dereference /snap/core/12725/usr/lib/snapd/info /media/mike/disk/usr/lib/snapd/info
1c1
< VERSION=2.54.3.2
---
> VERSION=2.54.2
Binary files /snap/core/12725/usr/lib/snapd/snap-bootstrap and /media/mike/disk/usr/lib/snapd/snap-bootstrap differ
Binary files /snap/core/12725/usr/lib/snapd/snap-confine and /media/mike/disk/usr/lib/snapd/snap-confine differ
Binary files /snap/core/12725/usr/lib/snapd/snapctl and /media/mike/disk/usr/lib/snapd/snapctl differ
Binary files /snap/core/12725/usr/lib/snapd/snapd and /media/mike/disk/usr/lib/snapd/snapd differ
Binary files /snap/core/12725/usr/lib/snapd/snap-device-helper and /media/mike/disk/usr/lib/snapd/snap-device-helper differ
Binary files /snap/core/12725/usr/lib/snapd/snap-discard-ns and /media/mike/disk/usr/lib/snapd/snap-discard-ns differ
Binary files /snap/core/12725/usr/lib/snapd/snap-exec and /media/mike/disk/usr/lib/snapd/snap-exec differ
Binary files /snap/core/12725/usr/lib/snapd/snap-failure and /media/mike/disk/usr/lib/snapd/snap-failure differ
Binary files /snap/core/12725/usr/lib/snapd/snap-gdbserver-shim and /media/mike/disk/usr/lib/snapd/snap-gdbserver-shim differ
Binary files /snap/core/12725/usr/lib/snapd/snap-gdb-shim and /media/mike/disk/usr/lib/snapd/snap-gdb-shim differ
Binary files /snap/core/12725/usr/lib/snapd/snap-preseed and /media/mike/disk/usr/lib/snapd/snap-preseed differ
Binary files /snap/core/12725/usr/lib/snapd/snap-recovery-chooser and /media/mike/disk/usr/lib/snapd/snap-recovery-chooser differ
Binary files /snap/core/12725/usr/lib/snapd/snap-repair and /media/mike/disk/usr/lib/snapd/snap-repair differ
Binary files /snap/core/12725/usr/lib/snapd/snap-seccomp and /media/mike/disk/usr/lib/snapd/snap-seccomp differ
Binary files /snap/core/12725/usr/lib/snapd/snap-update-ns and /media/mike/disk/usr/lib/snapd/snap-update-ns differ
Binary files /snap/core/12725/usr/lib/snapd/system-shutdown and /media/mike/disk/usr/lib/snapd/system-shutdown differ
Binary files /snap/core/12725/usr/lib/systemd/system-environment-generators/snapd-env-generator and /media/mike/disk/usr/lib/systemd/system-environment-generators/snapd-env-generator differ
Binary files /snap/core/12725/usr/share/doc/snapd/changelog.gz and /media/mike/disk/usr/share/doc/snapd/changelog.gz differ
Binary files /snap/core/12725/usr/share/doc/snapd/copyright.gz and /media/mike/disk/usr/share/doc/snapd/copyright.gz differ
diff -r --no-dereference /snap/core/12725/usr/share/snappy/dpkg.list /media/mike/disk/usr/share/snappy/dpkg.list
259c259
< ii  snapd                         2.54.3                             amd64        Daemon and tooling that enable snap packages
---
> ii  snapd                         2.54.2                             amd64        Daemon and tooling that enable snap packages
276c276
< ii  ubuntu-core-snapd-units       2.54.3                             all          transitional dummy package
---
> ii  ubuntu-core-snapd-units       2.54.2                             all          transitional dummy package
diff -r --no-dereference /snap/core/12725/usr/share/snappy/dpkg.yaml /media/mike/disk/usr/share/snappy/dpkg.yaml
258c258
< - snapd=2.54.3
---
> - snapd=2.54.2
275c275
< - ubuntu-core-snapd-units=2.54.3
---
> - ubuntu-core-snapd-units=2.54.2

```

So it appears this is an updated version of /snap/core/, probably, but I have no explanation for why it showed up as an external removable drive. This gives me some comfort that I'm less concerned it's some new exploit hooking into my computer, and more likely to be a fluke.

---

### Post by Mike_Schmidt on 2022-02-17
Maybe a final update.

I rebooted the computer and ran ```
apt update && apt upgrade -y && apt autoremove -y
```. It upgraded only one package, snapd. The new /snap/core is now version 2.54.3 (formerly only in the removable drive) and there is no longer a removable drive.

So thank you for your responses. Thank you also for your continued service to fellow Ubuntu users. It's really valuable and appreciated, especially when we just google for your knowledge and use it without comment. Respect and very best wishes to you with many beans.

I'm calling this fixed and moving on.

---

### Post by yetimon_64 on 2022-02-17
> **Mike_Schmidt said:**
> ...I'm calling this fixed and moving on.

Could you also mark it in the forum as [SOLVED] please? There is a link in my signature for how to mark a thread solved, if needed.

Regards, yeti.

---

