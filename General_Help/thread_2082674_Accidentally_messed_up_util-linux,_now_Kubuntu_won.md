---
title: "Accidentally messed up util-linux, now Kubuntu won't boot"
date: 2012-11-10
forum: General Help
---

### Post by Stonecold1995 on 2012-11-10
I tried compiling util-linux (version 2.22-rc2) from source and I used "sudo checkinstall -D".  It wouldn't install so I ran "dpkg -i" on the .deb file it created, and (stupidly) forced it to install.  It sort of installed, but some commands like fsck didn't work, so I tried uninstalling it.  Running "sudo apt-get install --reinstall util-linux" gave this:
```
apt-get install --reinstall util-linux
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of util-linux is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

and "sudo apt-get install util-linux" said it was already installed.  I rebooted and now my computer won't boot.  After I enter my encryption password, this line appeared (I'm not using a boot splash):
```
mount: /lib/x86_64-linux-gnu/libmount.so.1: version `MOUNT_2.21' not found (required by mount)
```
Then it shut down, and my computer won't boot.

How do I force a reinstall of util-linux?

**EDIT:** I sent a copy of "/bin/mount" from my other laptop to this one, and that allowed it to boot up successfully, although it was pretty unstable.  From there I reinstalled bsdutils and bsdmainutils and now it seems to be working again.

---

