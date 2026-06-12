---
title: "In emergency mode after installing windows and running Boot-Repair"
date: 2020-09-23
forum: General Help
---

### Post by makem2 on 2020-09-23
I have reinstalled windows thinking I could repair the boot but not so.

```

0.8608431] Couldn get size:0x800000000000000e
/dev.sda2: recovering journal
/dev/sda2: clean 376538/1250928, 4138042/4999936 blocks
[ 3.144058] PKCS#7 signature not signed with a trusted key
[ 3.278388] PKCS#7 signature not signed with a trusted key
[ 3.280587] PKCS#7 signature not signed with a trusted key
[ 3.335722] Bluetooth: hc10: unexpected event for gpcode 0xfc2f
[ 3.532775] PKCS#7 signature not signed with a trusted key
You are in emergency mode. After ;ogging in type "journalctl -xb" to view
system logs, "systemctlreboot" to reboot, "systemctl default" or "exit"
to boot into default mode
Press enter for maintainance
(or press Control-D to continue):

```

I have tried the above possible thinsg but to no good.

Boot-Repair gave me a working boot which includes the new windows.

I have tried in modes mentioned above but come up against sda2 being mounted and busy when attempt made to umount. fsck worked on sda1.

Can I get assistance in how to check the file system with fsck?

[https://paste.ubuntu.com/p/TPkm8QkH24/](https://paste.ubuntu.com/p/TPkm8QkH24/)

---

### Post by oldfred on 2020-09-23
Already posted here:
[https://ubuntuforums.org/showthread.php?t=2450815&p=13988302#post13988302](https://ubuntuforums.org/showthread.php?t=2450815&p=13988302#post13988302)

---

