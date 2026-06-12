---
title: "&quot;Error: Initrd too big&quot; after GRUB menu"
date: 2019-01-09
forum: General Help
---

### Post by jamarj on 2019-01-09
Good morning all,
Unexpectedly a server where I was working remotely rebooted and after that, it stopped responding via network.
I went to connect directly to it, and found that the server is getting stuck after GRUB menu with the following message:
"Error: initrd too big"

Now it is impossible to enter in any of the kernels or recovery mode.
Ubuntu version 16.04.5

**Actions that I have done so far:**

1) Boot from a liveCD and mount the filesystem and do a chroot. I have found that a new kernel was putted in the system on 21 December 2018 (so maybe the problem comes from here, because the server is ON from November with no shut-downs or reboots until the unexpected reboot of yesterday). The kernel version is 4.15.0-43-generic
2) I did sudo update-initramfs -c -k 4.15.0-43-generic but the error persists.
3) I have cleared old kernels with apt-get autoremove and what is left is:
linux-image-4.15.0-36-generic
linux-image-4.15.0-42-generic
linux-image-4.15.0-43-generic
linux-image-generic-hwe-16.04
But the error persists.

So, I'm open to try new ideas or procedures. Take into account that I'm not an expert about linux systems.

Thank you.

---

### Post by dbergst on 2019-01-09
There may be a few useful things to try in this bug report:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/429898](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/429898)

---

### Post by jamarj on 2019-01-10
> **dbergst said:**
> There may be a few useful things to try in this bug report:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/429898](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/429898)

I was not able to find the option in my bios. But I suspect that the issue is not related to memory, because the system keeps seeing the 64GB and memtest86 reports that all is fine.

What I found from booting in recovery mode is the following new information:
[IMG]https://i.stack.imgur.com/TiT64.jpg[/IMG]

---

