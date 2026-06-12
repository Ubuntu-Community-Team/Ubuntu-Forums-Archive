---
title: "is there a way to do a complete backup?"
date: 2007-03-24
forum: General Help
---

### Post by pixeldotz on 2007-03-24
i'm thinking about doing a dualboot scenario, but was wondering if there was away to do a complete backup so when i reinstall ubuntu i can just copy everything back and have it as it was. reason i ask is because my laptop took some setting up to get to work almost perfectly. 
ndiswrapper
alsa from scratch
915resolution

the wrapper and 915 wasn't a problem but ndis proved tedious :)

any help is greatly appreciated.

---

### Post by rogblake on 2007-03-25
> **pixeldotz said:**
> i'm thinking about doing a dualboot scenario, but was wondering if there was away to do a complete backup so when i reinstall ubuntu i can just copy everything back and have it as it was.

There are probably a number of ways to do this, the way I've always done it is to boot the system up in single-user mode, cd to the root directory, and use "cp -a" to copy the needed directories to the target drive. In general you will want to copy everything with the exception of psuedo-filesystems such as /proc. When you restore the system you will also need to re-install the bootloader and, if your partition layout differs from original, edit your /etc/fstab as needed.

The Linux Documentation Project's "Hard Disk Upgrade Mini How-To" describes how to copy a Linux system to another hard drive. It is fairly old (circa 2000) and only has instructions for the LILO bootloader, but describes the basic technique:

[http://tldp.org/HOWTO/Hard-Disk-Upgrade/index.html](http://tldp.org/HOWTO/Hard-Disk-Upgrade/index.html)

---

### Post by mac.ryan on 2007-03-25
I am not sure I understood you correctly, so forgive me if the following won't be of any use to you...

If your computer is currently running only ubuntu, and you would like now to get windows too, then I think you don't need to scrap the current installation. IMO it would be enough to:[LIST=1]
[*]Launch the LiveCD and shrink the ubuntu partition
[*]Created a NTFS partition in the freed space
[*]Install windows
[*]From the LiveCD, install Grub to get the dual boot working[/LIST]The procedure should be straight-forward but the last passage, but this page might help you: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

According to the partition scheme you chose, you might also wish to relocate the swap partition in order to keep it physically close to the shrunk ubuntu partition.

---

