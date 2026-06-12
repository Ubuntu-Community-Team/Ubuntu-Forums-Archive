---
title: "Internal drive partitions listed as removable"
date: 2020-09-25
forum: General Help
---

### Post by argon-1511 on 2020-09-25
I just installed Lubuntu today on an HP Stream laptop.  At the drives setup page there was no option to "Erase disk"  so I manually partitioned swap, UEFI, and the remaining space as an ext4 mounted to /.  I finished the install.   While ejecting a USB drive that I used to transfer an image, I noticed that my UEFI partition and main partition were listed as "Removable Media" in the taskbar widget.  Is there any way to set the drives to non-removable in Terminal so they don't appear in the widget?

This is my first experience installing any Linux distro.

---

### Post by guiverc on 2020-09-25
What release of Lubuntu are you talking about?

The last four releases of Lubuntu use the LXQt desktop, and installs by default don't install swap by default; most users don't use it using Lubuntu as it's light & fast on modern hardware, though for others like myself with older or less powerful hardware swap is of huge benefit. Swapfiles though are usually used over swap partitions though as easily changed (enabled/disabled/erased/created).

Releases prior to the last four, or Lubuntu 18.04 LTS & before used swap partition however, however even 18.04 could use swapfiles too.

Your question as to removal, I'd like to know your desktop & release details (legacy? modern?)

I'll provide some Lubuntu links too, in case of benefit

Lubuntu Manual - [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)
Lubuntu Links page - [https://lubuntu.me/%20links/](https://lubuntu.me/%20links/)
Lubuntu's main page - [https://lubuntu.me/](https://lubuntu.me/)

If I knew your release, I'd probably have also provided the release notes, as some release notes do cover clues to get around conditions where the "*Erase disk and install**" doesn't show.

---

### Post by argon-1511 on 2020-09-25
I'm running 20.04, the newest LTR as far as I know.  The computer I'm running it on is new, but low spec.  I installed swap in the partition setup because I figured it'd lighten the load on 4 gigs of RAM.  Swap is the only of the three partitions that doesn't show up.  

The desktop is stock 20.04.

---

### Post by Impavidus on 2020-09-26
The EFI and root partitions shouldn't be listed as removable storage (but may be listed as such while in the live session). To get some data, try```
sudo blkid
cat /etc/fstab
findmnt
```
Run those commands in a terminal and paste the output in the forum in code tags, like I did above.

---

### Post by argon-1511 on 2020-09-26
> **Impavidus said:**
> 
Run those commands in a terminal and paste the output in the forum in code tags, like I did above.


```
/dev/mmcblk0p1: UUID="6f4ff2e9-1301-42f2-a5e1-a2e2d1986931" TYPE="swap" PARTUUID="5c35c774-b345-d14a-8323-32d2e69b02aa"
/dev/mmcblk0p2: UUID="3A51-BAA6" TYPE="vfat" PARTUUID="9d974070-ebe7-a445-a4a1-81098e315869"
/dev/mmcblk0p3: UUID="d9128124-7c5a-4d79-b247-3391b515eb8f" TYPE="ext4" PARTUUID="beed86cf-e23a-c641-8073-341b88b10940"
```


Should I consider reinstalling or tackle each issue?  Other than these, the machine works fine.

---

### Post by TheFu on 2020-09-26
There is a setting in the fstab for each mount that can make them not show up in any GVFS-type GUI program.  I don't know if Qt supports that or not.  It would start with x- ..... in the fstab.  Need to see the actual fstab file to be more specific.

BTW, Lubuntu is NOT "stock ubuntu".  It is "stock Lubuntu" which is very different from a GUI perspective. Some libraries are different too, because Gnome isn't the preferred toolkit, Qt is. That shifts all sorts of things over to the KDE way of working.  To lesson RAM use, best to choose the KDE options.

Hibernation is out of favor for a number of reasons. Standby is preferred. Neither should be used if you care about security without every specific limitations.  For example, never use standby or hibernation when moving a system between buildings.

---

### Post by Impavidus on 2020-09-26
And the other two commands? Note that I fixed a typo in one of them. I never see any mounts that I configured in fstab show up in any GUI tools (in particular thunar), just setting mount options to defaults (more or less).

Hibernation is a different issue and I suggest one issue per thread, as it's unrelated. But hibernation only works if you first enable it and it's indeed out of favour, so maybe you don't want it fixed at all.

---

### Post by argon-1511 on 2020-09-26
> **Impavidus said:**
> And the other two commands? Note that I fixed a typo in one of them. I never see any mounts that I configured in fstab show up in any GUI tools (in particular thunar), just setting mount options to defaults (more or less).
[B]
Hibernation is a different issue and I suggest one issue per thread, as it's unrelated[/B]. But hibernation only works if you first enable it and it's indeed out of favour, so maybe you don't want it fixed at all.

Fair enough, other issue stricken from thread.

Other two commands:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=6f4ff2e9-1301-42f2-a5e1-a2e2d1986931 swap           swap    defaults   0 2
UUID=3A51-BAA6                            /boot/efi      vfat    umask=0077 0 2
UUID=d9128124-7c5a-4d79-b247-3391b515eb8f /              ext4    defaults   0 1

```

```
TARGET                                SOURCE     FSTYPE OPTIONS
/                                     /dev/mmcblk0p3
&#9474;                                                ext4   rw,relatime
&#9500;&#9472;/sys                                sysfs      sysfs  rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/kernel/security              securityfs securi rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/fs/cgroup                    tmpfs      tmpfs  ro,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/unified          cgroup2    cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/systemd          cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/hugetlb          cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/perf_event       cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpu,cpuacct      cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/blkio            cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/freezer          cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/memory           cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpuset           cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/devices          cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/net_cls,net_prio cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/rdma             cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9474; &#9492;&#9472;/sys/fs/cgroup/pids             cgroup     cgroup rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/fs/pstore                    pstore     pstore rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars         efivarfs   efivar rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/fs/bpf                       none       bpf    rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/kernel/debug                 debugfs    debugf rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/kernel/tracing               tracefs    tracef rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/sys/kernel/config                configfs   config rw,nosuid,nodev,noexe
&#9474; &#9492;&#9472;/sys/fs/fuse/connections          fusectl    fusect rw,nosuid,nodev,noexe
&#9500;&#9472;/proc                               proc       proc   rw,nosuid,nodev,noexe
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc          systemd-1  autofs rw,relatime,fd=28,pgr
&#9500;&#9472;/dev                                udev       devtmp rw,nosuid,noexec,rela
&#9474; &#9500;&#9472;/dev/pts                          devpts     devpts rw,nosuid,noexec,rela
&#9474; &#9500;&#9472;/dev/shm                          tmpfs      tmpfs  rw,nosuid,nodev
&#9474; &#9500;&#9472;/dev/mqueue                       mqueue     mqueue rw,nosuid,nodev,noexe
&#9474; &#9492;&#9472;/dev/hugepages                    hugetlbfs  hugetl rw,relatime,pagesize=
&#9500;&#9472;/run                                tmpfs      tmpfs  rw,nosuid,nodev,noexe
&#9474; &#9500;&#9472;/run/lock                         tmpfs      tmpfs  rw,nosuid,nodev,noexe
&#9474; &#9492;&#9472;/run/user/1000                    tmpfs      tmpfs  rw,nosuid,nodev,relat
&#9474;   &#9492;&#9472;/run/user/1000/gvfs             gvfsd-fuse fuse.g rw,nosuid,nodev,relat
&#9492;&#9472;/boot/efi                           /dev/mmcblk0p2
                                                 vfat   rw,relatime,fmask=007
```

---

### Post by Impavidus on 2020-09-26
Most of it looks OK, but the line in your /etc/fstab for your swap partition is a bit weird. That may confuse the file manager, that's supposed to list the various filesystems *except* those listed in /etc/fstab. For comparison, my /etc/fstab wasn't modified since a fresh install of Xubuntu 20.04 back in July and has this line for the swap partition:```
UUID=7a68be87-d091-478c-8165-47d994cd9c06 none            swap    sw              0       0
```
The swap partition isn't really mounted, so its mountpoint is set to none. Type is swap, options sw, dump and pass are set to 0. There's no filesystem, so no need to check it on boot or set a read-write option.

---

### Post by TheFu on 2020-09-26
+1 on swap --> none for the mount point and
+1 for the last '2' being a '0' for both swap AND the EFI partition.  The meaning of those numbers is spelled out in the fstab manpage, BTW.

I don't know that order of the file is important, but may try moving the swap to the bottom, so if there is any issue with that line, the other lines shouldn't be impacted or misinterpreted. 

I didn't check the UUID --> device mapping.  I haven't used UUIDs in some time because with LVM, the paths don't change and those paths are useful for humans, unlike UUIDs. If not using LVM, I suppose UUIDs is the next best method.

---

### Post by argon-1511 on 2020-09-26
If I were to reinstall, what would I change in the partition manager to resolve the ejectable drive issue?

This isn't my main computer, so wiping and reinstalling is relatively easy.

---

### Post by TheFu on 2020-09-26
I think it is probably a bug in whatever program is being used by Lubuntu to display this stuff. Is that Thunar? 
I say this assuming the fstab file shown is the correct file with the correct options.  

There is an x- .... set of comments (really fake options) that gvfs, udisks* and other gnome tools use to decide some behaviors.  Those tools _should_ use different configuration files for their needs, not bastardize the fstab file. I don't know where to get the full list of these abominations. Perhaps udisks manpage or buried somewhere in the gnome documentation at freedesktop.org?

Searching .... 
Google found this list of programs: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/desktop_migration_and_administration_guide/gvfs-tools-xdg-utils](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/desktop_migration_and_administration_guide/gvfs-tools-xdg-utils)
My 16.04 systems don't have any gvfs-*. The mount one seems related to [https://developer.gnome.org/gio/stable/gio.html](https://developer.gnome.org/gio/stable/gio.html)  16.04 doesn't have any gio at all either.

But on 20.04, there are a bunch of both commands. 
When I run, **gvfs-mount --list** I get a deprecation warning saying to use "gio mount" instead, with some output that isn't anything like what I'd expect needed to mount stuff.

When I run **gio mount --list**, notice it is gio as the command, mount as an option with --list as the 2nd option, the same output, which doesn't contain anything useful to put into a normal "mount" command, is shown.
**gio mount --list --detail ** does show details for each available volume.  Three of the items are 
[LIST=1]
[*]is_removable=1 and 
[*]is_media_removable=1
[*]can_eject=1
[/LIST]
It is shown for a fake CDROM, but not for other devices. Those both have
[LIST=1]
[*]  is_removable=0
[*]  is_media_removable=0
[*]can_eject=0
[/LIST]
which is expected. Perhaps Thunar is seeing these toggles on your system?  You might run **gio mount --list --detail** to see.  I have no idea how those are being set.  My BIOS does have settings for hot-swap devices, but I don't have 20.04 running on any physical hardware that would have the gio command, so I cannot check.

Thanks for this simple question. It got me too look much deeper into gvfs and gio subsystems. Didn't find an answer, but perhaps a lead for an answer?

---

### Post by argon-1511 on 2020-09-26
I appreciate the help.  

I just reinstalled after troubleshooting the cause of "erase disk and install" option being absent from my original installation.  I wanted to be sure that my inexperienced fumbling with the partition menu was not the cause of this issue. 

It wasn't.  The two partitions created automatically by the installer both display as ejectable... despite the drive being soldered to the board.  Maybe it's a quirk of the hardware?  This isn't exactly a top tier PC.

I'm just going to try and remove the GUI widget for the time being.

---

### Post by guiverc on 2020-09-26
> **TheFu said:**
> I think it is probably a bug in whatever program is being used by Lubuntu to display this stuff. Is that Thunar? 
I say this assuming the fstab file shown is the correct file with the correct options.  


FYI only

Lubuntu/LXDE used `pcmanfm` to handle the desktop/GUI & as a file manager
Lubuntu /LXQt uses `pcmanfm-qt` to handle the desktop/GUI & as a file manager
Panel is handled by `lxqt-panel` (but conf file is the ~same in live & installed systems)

On installed systems I wouldn't expect any / or /boot/efi (ESP) partitions to be ejectable, however they are on a *live* system prior to installation.  I don't know the *key/trigger* that makes it show on *live* and not on installed systems, that maybe the fix.

---

### Post by oldfred on 2020-09-26
> /dev/mmcblk0p1

While many tablet type systems use MMC as drive, the MMC card is normally the removeable card in your camera or other prtable device. Assuming it is removable is probably the error.

[https://en.wikipedia.org/wiki/MultiMediaCard](https://en.wikipedia.org/wiki/MultiMediaCard)
Originally:
Usage   Portable devices

---

### Post by guiverc on 2020-09-27
Thanks @oldfred :)

I now see your point. I don't have devices with a block device that shows like /dev/mmcblk0p1 so can't test it :(


@argon-1511
If you'd like to file a bug @argon-1511, I'll take a look at it.   I don't see bugs reported upstream relevant ([https://github.com/lxqt/pcmanfm-qt/issues](https://github.com/lxqt/pcmanfm-qt/issues) or [https://github.com/lxqt/lxqt-panel/issues](https://github.com/lxqt/lxqt-panel/issues)) but I'll ask on #lubuntu-devel to see if anyone in the team has something like it.

If you'd like to file a bug, you'll need a launchpad account, and can file with

```
ubuntu-bug lxqt-panel
```

For more information on Lubuntu bugs, I'll provide our wiki page ([https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/))

---

### Post by TheFu on 2020-09-27
Anyone with a Raspberry-Pi running Lubuntu could check this. Here's what it looks like on a r-pi v2 with a microSD and NFS mount with rasbian:
```
$ df -Th
Filesystem          Type      Size  Used Avail Use% Mounted on
/dev/mmcblk0p2      ext4       30G  7.1G   21G  26% /
/dev/mmcblk0p1      vfat      240M   39M  201M  17% /boot
romulus:/raid/media nfs       1.8T  1.7T   42G  98% /R
```

Unfortunately, 
```
$ gio mount --list
-bash: gio: command not found

```

---

