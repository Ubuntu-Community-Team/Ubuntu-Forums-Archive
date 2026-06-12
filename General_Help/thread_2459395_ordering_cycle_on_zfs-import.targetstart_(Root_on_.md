---
title: "ordering cycle on zfs-import.target/start (Root on ZFS)"
date: 2021-03-17
forum: General Help
---

### Post by andreralcantara on 2021-03-17
Hello!

If that's not the right place to post, feel free to direct me.

In summary, I'd like to know how to fix ZFS so that is starts properly on my system. There are lots of information spread out, and I'm not sure which to follow. Any help would be appreciated.

I have little experience with ZFS and even less with systemd (though it's always running, I rarely mess with it).

**The Problem:**

So, it's been a few months, I have this problem where ZFS doesn't start properly.

I have Xubuntu 20.04.2 and installed root on ZFS following these [instructions]("https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html#ubuntu-installer") (including the switch to an encrypted swap).

About what I have already found, it seems to be a bug, and there's lots of information about it at lots of differents places. According to [this]("https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1875577/comments/21"), it looks like this problem was fixed already on zfs-linux 0.8.4, however, using the packages available in apt, I can only install version 0.8.3.

Some options I have considered ([source]("https://bugs.gentoo.org/716488")):


[LIST]
[*]Finding a .deb file and updating ZFS to 0.8.4 (which packages would I need to upgrade?)
[*]Switching to mount generators (I'm not sure exactly how this would work, links would help a lot)
[/LIST]

Also, it seems like my boot partition is not mounted.

**Outputs:**

```

$ apt search zfs | grep installed
libuutil1linux/focal-updates,now 0.8.3-1ubuntu12.6 amd64 [installed]
libzfs2linux/focal-updates,now 0.8.3-1ubuntu12.6 amd64 [installed]
libzpool2linux/focal-updates,now 0.8.3-1ubuntu12.6 amd64 [installed]
parted/focal-updates,now 3.3-4ubuntu0.20.04.1 amd64 [installed,automatic]
zfs-initramfs/focal-updates,now 0.8.3-1ubuntu12.6 amd64 [installed]
zfs-zed/focal-updates,now 0.8.3-1ubuntu12.6 amd64 [installed]
zfsutils-linux/focal-updates,now 0.8.3-1ubuntu12.6 amd64 [installed]
zsys/focal-updates,now 0.4.8 amd64 [installed]

```

```

$ ls -l /etc/zfs/zfs-list.cache/
-rw-r--r-- 1 root root  163 jan 14 15:55 bpool
-rw-r--r-- 1 root root 2026 jan 18 17:48 rpool

```

```

$ sudo zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
rpool   218G  89,0G   129G        -         -    25%    40%  1.00x    ONLINE  -

```

Journald:

```

mar 17 19:00:39 systemd[1]: cryptsetup.target: Found ordering cycle on systemd-cryptsetup@swap.service/start
mar 17 19:00:39 systemd[1]: cryptsetup.target: Found dependency on systemd-random-seed.service/start
mar 17 19:00:39 systemd[1]: cryptsetup.target: Found dependency on zfs-mount.service/start
mar 17 19:00:39 systemd[1]: cryptsetup.target: Found dependency on zfs-import.target/start
mar 17 19:00:39 systemd[1]: cryptsetup.target: Found dependency on zfs-import-cache.service/start
mar 17 19:00:39 systemd[1]: cryptsetup.target: Found dependency on cryptsetup.target/start
mar 17 19:00:39 systemd[1]: cryptsetup.target: Job systemd-cryptsetup@swap.service/start deleted to break ordering cycle starting with cryptsetup.target/start
mar 17 19:00:39 systemd[1]: Unnecessary job for /dev/disk/by-id/ata-CT240BX500SSD1_2028E40641DE-part5 was removed.
...
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found ordering cycle on zfs-import.target/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on zfs-import-cache.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on cryptsetup.target/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on systemd-cryptsetup@swap.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on systemd-random-seed.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on zfs-mount.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Job zfs-import.target/start deleted to break ordering cycle starting with zfs-mount.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found ordering cycle on zfs-import.target/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on zfs-import-cache.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on cryptsetup.target/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on systemd-cryptsetup@swap.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on systemd-random-seed.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Found dependency on zfs-mount.service/start
mar 17 19:00:40 systemd[1]: zfs-mount.service: Job cryptsetup.target/start deleted to break ordering cycle starting with zfs-mount.service/start
...
mar 17 19:00:41 systemd[1]: Starting Install ZFS kernel module...
mar 17 19:00:41 systemd[1]: Finished Install ZFS kernel module.
mar 17 19:00:41 systemd[1]: Starting Import ZFS pools by cache file...
mar 17 19:00:41 systemd[1]: Started File System Check Daemon to report status.
mar 17 19:00:41 zpool[1172]: no pools available to import
mar 17 19:00:41 systemd[1]: Finished Import ZFS pools by cache file.
mar 17 19:00:41 systemd[1]: Reached target ZFS pool import target.
mar 17 19:00:41 systemd[1]: boot.mount: Directory /boot to mount over is not empty, mounting anyway.
mar 17 19:00:41 systemd[1]: Mounting /boot...
mar 17 19:00:41 systemd[1]: Starting Load ZFS key for rpool...
mar 17 19:00:41 systemd[1]: Starting Wait for ZFS Volume (zvol) links in /dev...
mar 17 19:00:41 systemd-fsck[1174]: fsck.fat 4.1 (2017-01-24)
mar 17 19:00:41 systemd-fsck[1174]: /dev/sda1: 293 files, 1812/130812 clusters
mar 17 19:00:41 systemd[1]: Finished File System Check on /dev/disk/by-uuid/9C15-64DA.
mar 17 19:00:41 mount[1178]: filesystem 'bpool/BOOT/ubuntu_p5vp3k' cannot be mounted, unable to open the dataset
mar 17 19:00:41 systemd[1]: boot.mount: Mount process exited, code=exited, status=1/FAILURE
mar 17 19:00:41 systemd[1]: boot.mount: Failed with result 'exit-code'.
mar 17 19:00:41 systemd[1]: Failed to mount /boot.
mar 17 19:00:41 systemd[1]: Dependency failed for Unattended Upgrades Shutdown.
mar 17 19:00:41 systemd[1]: unattended-upgrades.service: Job unattended-upgrades.service/start failed with result 'dependency'.
mar 17 19:00:41 systemd[1]: Dependency failed for /boot/efi.
mar 17 19:00:41 systemd[1]: Dependency failed for Local File Systems.
mar 17 19:00:41 systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
mar 17 19:00:41 systemd[1]: Dependency failed for /boot/grub.
mar 17 19:00:41 systemd[1]: boot-grub.mount: Job boot-grub.mount/start failed with result 'dependency'.
mar 17 19:00:41 systemd[1]: boot-efi.mount: Job boot-efi.mount/start failed with result 'dependency'.

```

Cya

---

### Post by andreralcantara on 2021-03-19
Bumping.

---

### Post by DuckHook on 2021-03-19
Welcome to the Forums, andreralcantara,

I'm no ZFS expert. I do use it, but I'm having difficulty understanding what your problem is.

[LIST=1]
[*]Does it not boot?
[*]Why do you feel that you need ZFS?
[*]If you want a fully-encrypted disk, the default in Ubuntu is LVM, not ZFS. Using LVM, you can choose to encrypt at initial install.
[*]A full ZFS install also makes bpool for the boot sector. Since I don't see this in your zpool list, I assume that your conversion was not complete.
[*]If you are intent on full disk ZFS, I would suggest that, instead of trying to convert an existing install, you do a new install from scratch and choose a ZFS install. Let the installer create the needed underlying infrastructure instead of trying to back them in later.
[*]I have no idea how full disk encryption coexists with ZFS. Can't help you there.
[*]Note that my ZFS installs all have the very irritating default of snapshotting the slightest change to the system. Since I do almost daily update/full-upgrades, this quickly fills up my main disk. I have had to disable this "feature" and delete a ridiculous number of snapshots to make my ZFS installs bearable.
[/LIST]

---

### Post by andreralcantara on 2021-03-20
Hello, I think I didn't explain the full-picture clearly (or at all hahaha).

First off, thanks a lot for answering me :)


[LIST=1]
[*]The machine does boot.
[*]I really liked the interface, so I decided to install my machine with it. I also wanted some features such as the disk encryption, compression and dedup.
[/LIST]

The installation was the automatic ZFS install from the Xubuntu installer (I believe there was an option during installation, which was marked as experimental). I made a modification to the installer though, so that rpool (root pool) could be encrypted. The modification is present [here]("https://linsomniac.gitlab.io/post/2020-04-09-ubuntu-2004-encrypted-zfs/").

I can't pinpoint what the problem is exactly. But I can tell you that previously, things were working normally, then one day, GRUB started to act in a weird way.


[LIST]
[*]GRUB menu usually appeared for 3 seconds and then the default choice was made (GRUB_TIMEOUT - I had configured it this way).
[*]After the problem, GRUB menu started appearing for 30s. Some error messages which were previously hidden ("Error Communicating to TPM chip") started appearing after I make my boot choice.
[/LIST]

After the GRUB changes, I investigated journald to check if there were any visible problems. And indeed, those errors indicating "ordering cycle" appeared. Some lines which I forgot to include say "Failed to mount /boot" (I will update the previous post with these messages).

Also, ZFS used to list both rpool and bpool previously. Now, it lists only rpool, which tells me that ZFS is failing to import bpool.

Digging through the logs:

[LIST]
[*]Jan 14th - System was installed
[*]Feb 16th - Packages were upgraded with "sudo apt upgrade --fix-missing". I don't remember the reason for "--fix-missing". ZFS packages were upgraded from 0.8.3-1ubuntu12.5 to 0.8.3-1ubuntu12.6.
[*]Feb 16th - After the upgrade and a system reboot, the problem starts appearing.
[/LIST]

Digging through other things:

- bpool is present on my system. It can be imported manually and contains the following files:

```

/mnt/boot$ find | sort | xargs ls -ld
drwxr-xr-x 4 root root       19 fev 16 20:17 .
-rw-r--r-- 1 root root   237764 jan 15 06:50 ./config-5.4.0-64-generic
-rw-r--r-- 1 root root   237764 jan 18 13:31 ./config-5.4.0-65-generic
drwxr-xr-x 2 root root        2 jan 14 15:13 ./efi
drwxr-xr-x 2 root root        2 jan 14 15:13 ./grub
lrwxrwxrwx 1 root root       27 fev 12 09:23 ./initrd.img -> initrd.img-5.4.0-65-generic
-rw-r--r-- 1 root root 83689842 fev 16 19:12 ./initrd.img-5.4.0-64-generic
-rw-r--r-- 1 root root 83705069 fev 16 19:15 ./initrd.img-5.4.0-65-generic
lrwxrwxrwx 1 root root       27 fev 12 09:23 ./initrd.img.old -> initrd.img-5.4.0-64-generic
-rw-r--r-- 1 root root   182704 ago 18  2020 ./memtest86+.bin
-rw-r--r-- 1 root root   184380 ago 18  2020 ./memtest86+.elf
-rw-r--r-- 1 root root   184884 ago 18  2020 ./memtest86+_multiboot.bin
-rw------- 1 root root  4746296 jan 15 06:50 ./System.map-5.4.0-64-generic
-rw------- 1 root root  4746296 jan 18 13:31 ./System.map-5.4.0-65-generic
lrwxrwxrwx 1 root root       24 fev 12 09:23 ./vmlinuz -> vmlinuz-5.4.0-65-generic
-rw------- 1 root root 11686656 jan 15 06:56 ./vmlinuz-5.4.0-64-generic
-rw------- 1 root root 11686656 jan 18 13:45 ./vmlinuz-5.4.0-65-generic
lrwxrwxrwx 1 root root       24 fev 12 09:23 ./vmlinuz.old -> vmlinuz-5.4.0-64-generic

```

- The directory /boot is present in rpool with the following files:

```
/boot$ find | sort | xargs ls -ld
drwxr-xr-x 3 root root       11 mar 11 13:29 .
-rw-r--r-- 1 root root   237730 jan 27 18:44 ./config-5.4.0-66-generic
drwxr-xr-x 2 root root        5 mar 11 13:29 ./grub
-r--r--r-- 1 root root    16911 mar 11 13:29 ./grub/grub.cfg
-rw-r--r-- 1 root root     1024 mar 20 16:59 ./grub/grubenv
-rw-r--r-- 1 root root  2395475 fev 22 17:22 ./grub/unicode.pf2
lrwxrwxrwx 1 root root       27 mar  8 06:47 ./initrd.img -> initrd.img-5.4.0-66-generic
-rw-r--r-- 1 root root 83720314 mar 11 13:29 ./initrd.img-5.4.0-66-generic
lrwxrwxrwx 1 root root       27 mar  8 06:47 ./initrd.img.old -> initrd.img-5.4.0-66-generic
-rw------- 1 root root  4746873 jan 27 18:44 ./System.map-5.4.0-66-generic
lrwxrwxrwx 1 root root       24 mar  8 06:47 ./vmlinuz -> vmlinuz-5.4.0-66-generic
-rw------- 1 root root 11690752 jan 27 19:14 ./vmlinuz-5.4.0-66-generic
lrwxrwxrwx 1 root root       24 mar  8 06:47 ./vmlinuz.old -> vmlinuz-5.4.0-66-generic

```

---

### Post by DuckHook on 2021-03-20
Thanks for the clarifications.

As already stated, I can be of little further help to you here. The problem is that your install is highly customized to the point of being almost unique. I know of no one else who has tried to full&#8209;disk encrypt a ZFS install implemented after the fact. I would not dream of doing so, mainly because an excellent alternative already exists that works out of the box and achieves the same results. I don't believe in reinventing the wheel when others who are way smarter than me have already done the drudgery, squashed the bugs and automated the implementation to the point that I only have to select that option at time of install. I'm speaking of the aforementioned LVM&#8209;based full disk encryption.

Perhaps others here may have tried your implementation and can provide some guidance. Other than that, I can only suggest that you try visiting the Oracle forums (ZFS is mainly an Oracle beast), or the Red Hat forums, though those worthies have now turned their forums into a privatized members&#8209;only affair. You can sign up, I suppose.

A final thought:

If you are doing all of this for the sake of instruction, self&#8209;education, kicks and giggles, then I salute your intrepid spirit even if I can be of no assistance. But if you are simply after a fully encrypted install that gives you redundancy, snapshots, etc, then LVM will give you practically everything that ZFS will, but in a form that has now been done by countless others and has more than a chance of garnering you help on forums such as these, if only because it has precedent. A consideration.

---

### Post by andreralcantara on 2021-03-21
Thanks a lot for the help man. While yes, this first installation was mostly because I wanted to get used to ZFS, I will certainly keep LVM in mind (damn, if I were to install full-disk ZFS on someone else's machine that would probably be a stupid idea, unless very well justified). I really appreaciate your insights and the guidance.

---

