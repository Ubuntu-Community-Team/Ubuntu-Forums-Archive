---
title: "Fails to unmount / when shutting down (Xubuntu 12.10 64 bit)"
date: 2013-01-26
forum: General Help
---

### Post by Calinou on 2013-01-26
Hi,

when shutting down (I disabled the graphical splash screens), I can see the system unmounting partitions. However, the / partition fails to unmount every time I shut down since a few days ago. The only application I have open when shutting down is X-Chat, and quitting it before shutting down does not change anything to the problem. When booting, /dev/sda4 is always being reconstructed from the journal (ext4 partition of about 1.7TiB, contains /home), which makes booting slower (no data is lost, apparently).

---

### Post by Calinou on 2013-01-28
"Bump". :popcorn:

---

### Post by Karlchen on 2013-01-28
Hello, Calinou.

When did this problem start? Right after installing kernel 3.5.0-22 perhaps?
In a terminal window execute ```
uname -a
``` to determine the current kernel version.
In case the kernel version is 3.5.0-22, you may be interested in this thread:
**[Mint13-14 Latest Kernel Version Causing EXT4-fs Errors]("http://forums.linuxmint.com/viewtopic.php?f=47&t=123439")** and very likely in this [**Launchpad bug report**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1105900").
Do not assume Linux Mint 14 were unrelated to Ubuntu 12.10. They are pretty close relatives: Mint 14 is Ubuntu 12.10 minus the Ubuntu desktop environment plus the Linux Mint desktop environment (Cinnamon, xfce or Mate).
The same is true for Mint 13 which is closely related to Ubuntu 12.04.1.

Kind regards,
Karl

---

