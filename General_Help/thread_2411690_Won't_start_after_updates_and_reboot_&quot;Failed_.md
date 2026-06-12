---
title: "Won't start after updates and reboot: &quot;Failed to execute /init (error -2)&quot;"
date: 2019-02-02
forum: General Help
---

### Post by droux2 on 2019-02-02
Dedicated Ubuntu Desktop 18.04 (LTS) machine: after letting my machine run a few updates without a reboot, I finally let restart and now I am getting a kernel panic:
[INDENT][FONT=courier new]Couldn't get size: 0x800000000000000e
Failed to execute /init (error -2)
Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
...
---[ end Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.[/FONT][/INDENT]

Here's what I have done so far:
[LIST=1]
[*]Tried booting with older Kernels and in recovery mode from GRUB
[LIST=1]
[*]Same issue occurs with each kernel
[LIST=1]
[*]4.15.0-44
[*]4.15.0-43
[*]4.15.0-42
[*]3.19.0-33
[/LIST]
[/LIST]

[*]Ran boot-repair-disk
[LIST=1]
[*]Same issue occurs after finishing with the standard repair option
[*]The output from boot-repair is at [http://paste.ubuntu.com/p/Qdj6qfc843/](http://paste.ubuntu.com/p/Qdj6qfc843/)
[/LIST]

[*]Google / forum search
[LIST=1]
[*]Haven't found a solution for my issue
[/LIST]
[/LIST]

I've been looking over the suggested [https://www.kernel.org/doc/Documentation/admin-guide/init.rst](https://www.kernel.org/doc/Documentation/admin-guide/init.rst), but it did not clarify things for me (I've never compiled a kernel). Does anyone have any suggestions on how I can set an init= option with GRUB and what I should try setting it to (an example would be helpful!)?

---

### Post by droux2 on 2019-02-03
*Bump*

---

