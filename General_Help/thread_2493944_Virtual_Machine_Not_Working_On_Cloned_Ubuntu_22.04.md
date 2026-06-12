---
title: "Virtual Machine Not Working On Cloned Ubuntu 22.04"
date: 2023-12-30
forum: General Help
---

### Post by mikegreen8 on 2023-12-30
This is sort of a continuation of my previous Post:
[SIZE=1][https://ubuntuforums.org/showthread.php?t=2493921&p=14172305#post14172305](https://ubuntuforums.org/showthread.php?t=2493921&p=14172305#post14172305)[/SIZE]


With the help of this forum I was able to clone my MBR ubuntu Desktop onto a GPT ESATA. 

I built the ubuntu partition on the ESATA as follows:

1. Formatted an ESATA as GPT, and allocated an EXT4 partition.

2. Did a LIVE ubuntu ISO USB install onto the ESATA EXT4 partition

3. Booting with a USB, I rsync my ubuntu Desktop onto the ESATA EXT4 partition. In order to ensure the ESATA would boot, I Excluded the following files in the rsync command (--exclude-from=FILE). Here is the contents of the Exclude file:
[SIZE=1]- /boot
- /etc/fstab
- /etc/default/grub
- /etc/default/grub.d/*
- /etc/grub.d/*
- /etc/init.d/grub*
- /etc/pm/sleep.d/*grub-common
- /etc/kernel/post*.d/zz-update-grub
- /lib/systemd/system/grub*
- /usr/bin/grub*
- /usr/lib/grub-legacy/*
- /usr/sbin/*grub*
- /usr/share/bash-completion/completions/grub*
- /usr/share/bug/grub-pc/*
- /usr/share/doc/grub-pc
- /usr/share/man/man8/grub*
- /usr/lib/grub/*
- /usr/sbin/grub*
- /usr/share/apport/package-hooks/*grub2*
- /usr/share/bug/grub-common/*
- /usr/share/grub/*
- /usr/share/man/man*/grub-*
- /usr/share/doc/grub-gfxpayload-lists/*
- /usr/share/grub-gfxpayload-lists/*
- /usr/share/bug/grub-pc-bin/*
- /usr/share/lintian/overrides/grub-pc-bin
- /usr/share/bug/grub2-common/*
- /usr/share/grub/default/grub*
- /usr/share/info/grub*
[/SIZE]
I BIOS disabled my SATA ubuntu Desktop SATA, and booted the ESATA ubuntu - looks and feels identical to my Desktop  -  Except Virtual Machine is not working.

When I try to start my Windows 10 Vbox, I get 'Kernel Driver Not installed (rc = -1908)' - see attched pic.

Virtual Macine is in its own partition on my Desktop - I rsync the ENTIRE Virtual Machine partition from the Desktop over to a newly created partition on the ESATA.

Secure Boot is Enabled in the BIOS - it is greyed out so I can't change it.

When I boot from the Desktop SATA, VBox works fine. When I toggle over to the ESATA ubuntu I get the error.

I would not like to re-install VBox on the ESATA, as it was a lot of work for me to get a virtual WIN10 working.

Any thoughts ?
M...

---

### Post by MAFoElffen on 2023-12-30
This is a duplicate of your thread, that because it was dealing with a virtual, was moved to the Virtualization seciton: [https://ubuntuforums.org/showthread.php?t=2493945](https://ubuntuforums.org/showthread.php?t=2493945)

<<This one will most likely be CLOSED>>

---

### Post by deadflowr on 2023-12-30
closed

---

