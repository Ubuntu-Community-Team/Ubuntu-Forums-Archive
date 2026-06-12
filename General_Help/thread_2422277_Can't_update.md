---
title: "Can't update"
date: 2019-07-04
forum: General Help
---

### Post by DougieFresh4U on 2019-07-04
I am not sure what's going on but when I try to update I am getting a whole lot of text in terminal.
When I try:
sudo apt-get -f install
I'm getting a lot more text in terminal and I'm not very good at understanding what it all means.
Hopefully some one can point me in the right direction, please.
```
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 125 not upgraded.
W: Not using locking for read only lock file /var/lib/dpkg/lock-frontend
W: Not using locking for read only lock file /var/lib/dpkg/lock
W: chown to _apt:root of directory /var/cache/apt/archives/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0700 of directory /var/cache/apt/archives/partial failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chown to _apt:root of directory /var/lib/apt/lists/auxfiles failed - SetupAPTPartialDirectory (30: Read-only file system)
W: chmod 0700 of directory /var/lib/apt/lists/auxfiles failed - SetupAPTPartialDirectory (30: Read-only file system)
W: Not using locking for read only lock file /var/cache/apt/archives/lock

```

---

### Post by Bashing-om on 2019-07-04
DougieFresh4U; Humm ...

Another instance of package management active that has a "lock'' ??

what shows terminal command:
```

ps -e | grep apt

```

if here is a direct return to prompt - nothing is active;  Now what results:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]make the system happy
[/INDENT][/INDENT]

---

### Post by Impavidus on 2019-07-05
It says you've got a read-only filesystem. If this suddenly happened, there may have been an I/O error that caused the filesystem to be remounted read-only. Run a filesystem check. It may be done automatically at reboot. Also check the health of your hard drive. A failing hard drive can cause this issue, but your problem may also be something minor.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

BTW, 125 packages not upgraded is quite a lot.

---

### Post by DougieFresh4U on 2019-07-05
Thank to both of you for answering my issue.
I ran a manual fsck check from a 'live' boot. The first time it booted up after the run but it still
had issues trying to update. I rebooted computer and it would boot as before and the run manual fsck messege again.
So I booted from live USB again and ran manual fsck again, rebooted and all seems normal and I was allowed to update. 
All is good now. Google search was my friend in guiding me. Its been a long time since my system has gotten 'borked'
and it caught me off guard.
Thanks

---

