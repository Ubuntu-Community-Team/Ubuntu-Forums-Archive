---
title: "ubuntu-zfs package for 15.10 missing?"
date: 2015-10-23
forum: General Help
---

### Post by ryan-flagler on 2015-10-23
Installing 15.10 to troubleshoot a separate issue and noticed the ubuntu-zfs package hasn't been built for 15.10. Is this just because it's so fresh or is there a reason it's not available?

[https://launchpad.net/~zfs-native/+archive/ubuntu/stable?field.series_filter=wily](https://launchpad.net/~zfs-native/+archive/ubuntu/stable?field.series_filter=wily)

---

### Post by Maximilian_Kirchne on 2015-10-24
Did you manage to install it somehow? I have the same issue. For some reason even after adding the ppa I cannot even install zfs-linux though it says it has been build.

---

### Post by dajhorn on 2015-10-25
ZoL was imported by Ubuntu and is currently in the universe section:

* [http://packages.ubuntu.com/source/wily/spl-linux](http://packages.ubuntu.com/source/wily/spl-linux)
* [http://packages.ubuntu.com/source/wily/zfs-linux](http://packages.ubuntu.com/source/wily/zfs-linux)

The PPA probably won't publish an [FONT=Courier New]ubuntu-zfs[/FONT] package for Ubuntu 15.10 to avoid distro conflicts, most notably because Wily doesn't need enhanced [FONT=Courier New]mountall[/FONT] or [FONT=Courier New]dkms[/FONT] packages.

---

### Post by lukeiamyourfather on 2015-10-30
> **dajhorn said:**
> ZoL was imported by Ubuntu and is currently in the universe section:

* [http://packages.ubuntu.com/source/wily/spl-linux](http://packages.ubuntu.com/source/wily/spl-linux)
* [http://packages.ubuntu.com/source/wily/zfs-linux](http://packages.ubuntu.com/source/wily/zfs-linux)

The PPA probably won't publish an [FONT=Courier New]ubuntu-zfs[/FONT] package for Ubuntu 15.10 to avoid distro conflicts, most notably because Wily doesn't need enhanced [FONT=Courier New]mountall[/FONT] or [FONT=Courier New]dkms[/FONT] packages.

Thank you for the update! Does this mean moving forward (15.10 and up) users should install ZFS on Linux from the Ubuntu repositories instead of the PPA? Also thank you for the work you've done on the PPA and ZFS on Linux in the past. I've used it many times.

---

### Post by zfsraid on 2015-12-31
Having just been through this upgrade to 15.10, I can hopefully help those who still need to do so before 15.04 goes end of support.

My take is that yes, you can now use the Ubuntu Universe version, and that's what I've done. Be aware that it does mean a downgrade of ZoL from 0.6.5 to 0.6.4. As 0.6.5 contains some fixes for crashes, then if I experience any then I will probably look at going back to the PPA.

My server uses ZFS for its root filesystem, although I have a separate /boot as ext4. Below are the steps I needed to go through to upgrade from 15.04+PPA to 15.10.

[LIST]
[*]Ensure sufficient space in /tmp and /boot
[*]If you have ZFS as root, a snapshot clone makes a great precautionary backup:
[LIST]
[*]zfs snapshot raid/root@preupgrade
[*]zfs clone raid/root@preupgrade raid/preupgraderoot
[*](Above assumes that your root filesystem is called "root" in a pool named "raid")
[*](If you needed to use this backup, you would need to edit the grub kernel command line to refer to raid/preupgraderoot)
[/LIST]

[*]Comment or delete the ZFS PPA from your system's APT config
[*]do-release-upgrade (but don't reboot!)
[*]apt remove all the ZFS packages that came from the PPA
[*]apt install zfsutils-linux zfs-initramfs (this pulls in the Ubuntu ones)
[*]Double check that both dkms modules built without errors. My zfs-dkms complained that it couldn't find spl, until I removed and reinstalled the official ubuntu spl-dkms.
[*]Confirm that the initramfs has been updated with the new dkms (if not, do update-initramfs manually).
[*]systemctl enable zfs.target (so that zfs filesystems will be automounted on boot)
[*]apt purge all the remaining packages from the PPA that are listed as "rc" (config present) in "dpkg-query -l | grep 0.6.5". I needed to purge libzfs2 zfsutils ubuntu-zfs libzpool2 libuutil1 libnvpair1.
[*]Reboot
[/LIST]

Hopefully the above will have some useful pointers for people attempting the move. ZFS is a great filesystem and I think it's worth the initial trouble to get it set up.

---

