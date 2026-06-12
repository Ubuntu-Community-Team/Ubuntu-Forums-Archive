---
title: "Login screen freezes"
date: 2013-02-24
forum: General Help
---

### Post by mducky on 2013-02-24
Hi

I tried to install the latest amd graphics driver from their homepage three weeks ago which turned out to be a big mistake.

I'm going to describe my actual problem and then try to give an overview of what I have done so far.

When I boot my system, Ubuntu 12.10 x64 3.5.0-21, it doesn't respond to any user input (no mouse, no keyboard no tablet) so I can't login. After +/- 10 seconds it completely freezes. I can figure that out as the cursor in the login form stops blinking.

If I switch to an older kernel version e.g. 3.5.0-19, I am able to login so far but ubuntu is responding really slow, no dual-screen support etc. so I guess there is still a problem with the graphics driver. Every now and then, nautilus is experiencing an internal error but I can't view the details as the loading indicator runs forever. In dmesg I found the following:

```
[    8.121893] EXT4-fs (sdd6): INFO: recovery required on readonly filesystem
[    8.121896] EXT4-fs (sdd6): write access will be enabled during recovery
[    8.628785] EXT4-fs (sdd6): orphan cleanup on readonly fs
[    8.628794] EXT4-fs (sdd6): ext4_orphan_cleanup: deleting unreferenced inode 82182153
[    8.628856] EXT4-fs (sdd6): ext4_orphan_cleanup: deleting unreferenced inode 55837473
[    8.628878] EXT4-fs (sdd6): ext4_orphan_cleanup: deleting unreferenced inode 55837683
[    8.628891] EXT4-fs (sdd6): ext4_orphan_cleanup: deleting unreferenced inode 55837666
[    8.628902] EXT4-fs (sdd6): ext4_orphan_cleanup: deleting unreferenced inode 55837507
[    8.628913] EXT4-fs (sdd6): 5 orphan inodes deleted
[    8.628914] EXT4-fs (sdd6): recovery complete
[    8.707178] EXT4-fs (sdd6): mounted filesystem with ordered data mode. Opts: (null)
 
[...]
[   40.462574] EXT4-fs (sdd6): re-mounted. Opts: errors=remount-ro
```



**What happened**
I installed, uninstalled and reinstalled those amd fglrx drivers a few times, following advises from [here]("http://askubuntu.com/questions/97171/cant-install-fglrx-or-boot-computer") or [here]("http://ubuntuforums.org/showthread.php?t=1734508") as I experienced the same problems when trying to uninstall.

Then after some time, my system crashed while performing an update I think the package manager had some write lock on the filesystem. I had a lot of troubles then couldn't boot again because of [this]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error") error. I managed to get apt-get to run again via recovery console and the help from [here]("http://askubuntu.com/questions/109203/ubuntu-says-that-filesystem-is-read-only-when-trying-to-use-sudo-or-su") and some other pages. Basically when trying to update I got something like

```
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

I really don't want to reinstall ubuntu for a various reasons- one of them is having an activated matlab installation on that system.

I really appreciate any help. Thanks!

---

