---
title: "RAM or HDD problem?"
date: 2007-01-24
forum: General Help
---

### Post by Hexidigital on 2007-01-24
Hi all.

I ran into a problem two days ago:
I was SSHed into my server (Dapper) from school. After installing some updates, I rebooted and was not able to SSH in again. I had to get to my 6pm class, so I figured it could wait until I got home.

When I got home, I found my server in fact did not reboot, and there was an error on the screen about a possible ACPCI lock (?) preventing a power change. I thought nothing of it, and hard-reset it.

I woke up the next morning, began to check email, when the server locked again. I reset it, but this time, it wouldn't boot into a login prompt.

I was on #ubuntu on freenode, and was told to use memtest86+ from my LiveCD to test the memory -- which locked the server every time (and still does).

To rule out a possible hard disk failure, I also installed Smartmontools and ran smartctl -A /dev/hda and /dev/hdb, which showed my disks are "old_age" and "Pre-fail" states (which is wierd, because on my new laptop, it shows the same).

Any ideas what I could check next? I am afraid to keep my server running because I do not know what would happen should the memory or hard disks fail completely.

Any suggestions would be greatly appreciated!

---

### Post by Hexidigital on 2007-01-24
I was also wondering -- Is it possible for these problems to be related to the libc6 update?

---

