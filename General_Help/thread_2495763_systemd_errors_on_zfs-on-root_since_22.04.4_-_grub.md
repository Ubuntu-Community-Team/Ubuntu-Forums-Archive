---
title: "systemd errors on zfs-on-root since 22.04.4 - grub configuration issues?"
date: 2024-02-29
forum: General Help
---

### Post by chenel on 2024-02-29
Hello!

I'm running Ubuntu 22.04 with zfs on root and encrypted filesystems as set up by the 22.04 installer.  This worked great until recently, but something seems to have gotten mixed up when things automatically upgraded from 22.04.3 to 22.04.4.  It looks like that was released a week ago, but this is a laptop that I don't reboot that often (I typically suspend it for carrying back and forth to/from my office).  When I rebooted yesterday, I was dropped into the initramfs shell with "no pool was imported" errors.  I found that any of the kernel options that had been installed recently had this same behavior; but the only remaining kernel from pre-22.04.4 still booted ok.  Thinking that there must have been some interruption in grub update, I ran `update-grub` from this remaining working kernel.  That seems to have borked everything.  Now even the pre-22.04.4 kernel fails instead with 
```

error: can't find command `hwmatch'.
error: file `/@/boot/vmlinuz-[kernel number]' not found.
Loading initial ramdisk...
error: you need to load the kernel first.
Press any key to continue...

```

I since noticed that I have two sets of "Advanced options for Ubuntu" on my grub splash screen: one that just says "Advanced options for Ubuntu" and another that says "Advanced options for Ubuntu 22.04.4 LTS".  All the entries in the latter list will boot, but they all lock up after the initial splash screen where I enter my key to unlock the ZFS volumes.  After booting into recovery mode, I've discovered that what's happening is that they're locking up when logind is supposed to be taking over.  I disabled GDM (`systemctl disable gdm`) so that I can at least get to a usable shell.  But I see lots of ugly errors printed to the TTY before the login prompt appears.  Looking in the syslog, it turns out they're basically all from services `systemd` is trying to start up, and they all take this form:
```

[servicename].service: Failed to set up mount namespacing: /run/systemd/unit-root/[pathname]: No such file or directory
[servicename].service: Failed at step NAMESPACE spawning [path to service]: No such file or directory

```
where `[servicename]` includes some pretty important ones like `NetworkManager`, `resolved`, or `logind`.  `[pathname]` is one of the system ones: `etc`, `usr`, ...
However, I found I can start these all by hand if I want to, and they work fine.  e.g.:
```

sudo /usr/sbin/NetworkManager
sudo /lib/systemd/systemd-resolved &

```

I'm suspicious that the fundamental issue here is some kernel option passed via the Grub commandline that has to do with how the ZFS volumes are set up, since before I did update-grub, there was an old kernel version that booted and ran fine.  I started poking around in my `/boot/grub/grub.conf`, and discovered there are still some entries in there referencing `22.04.3`.  I've done some more poking around in `/etc/grub.d` to try to chase this down, and I discovered the existence of `10_linux_zfs_proxy`, which contains the out-of-date `22.04.3` entries.  Googling led me to understand that this comes about from `grub-customizer`; but I haven't used that at all myself, so I assume that the installer must have set this up for me.  It looks like this needs to be updated somehow---but how?  At this point I'm out of my depth (Grub and command-line kernel options have never been a strength of mine) and I couldn't quite find the right recipe to Google in order to get further.  (I found this forum post: [https://askubuntu.com/questions/1355032/after-using-grub-customizer-how-do-i-recover-the-zfs-grub2-menu-options-on-ubun](https://askubuntu.com/questions/1355032/after-using-grub-customizer-how-do-i-recover-the-zfs-grub2-menu-options-on-ubun) but this person seems to have used `grub-customizer` manually, and I certainly didn't.  So I'm reluctant to just blow away `grub-customizer` unless I know I don't really need it.)  Does anybody have any suggestions of what to try next?

p.s.  I did find these other forum posts, but none of them *quite* seems to match my situation:
[https://ubuntuforums.org/showthread.php?t=2486982](https://ubuntuforums.org/showthread.php?t=2486982)
[https://ubuntuforums.org/showthread.php?t=2494397](https://ubuntuforums.org/showthread.php?t=2494397)
[https://askubuntu.com/questions/1502826/how-do-i-fix-a-zfs-boot-problem-error-no-such-device](https://askubuntu.com/questions/1502826/how-do-i-fix-a-zfs-boot-problem-error-no-such-device)

---

