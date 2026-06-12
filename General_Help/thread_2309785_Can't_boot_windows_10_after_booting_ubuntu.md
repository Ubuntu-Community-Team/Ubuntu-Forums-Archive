---
title: "Can't boot windows 10 after booting ubuntu"
date: 2016-01-13
forum: General Help
---

### Post by dvdbillen on 2016-01-13
I've never seen this one. It's got me baffled:

- Alienware X51 R3 bundled with Windows 10

- Setup dual boot with Ubuntu 14 (Side note: Ubuntu has much fewer problems than Windows 10).

- Both systems are available from grub and they work - none of the usual problems.

- If I run Ubuntu then the next time I try to boot Windows 10 it fails and "locks up" at some apparently arbitrary point during login. I must cycle power. It fails again, (this time a black screen). I must cycle power. This time it boots to recovery mode. From recovery mode the option to continue and boot windows 10 works every time.

- It doesn't matter if I shutdown or reboot from Ubuntu. It doesn't matter if the machine was shut down and has been off all night.

- If I reboot after running Windows 10 it boots fine. It's only if the last thing I ran was Ubuntu.

- I've disabled fast startup and gone through the Windows "startup freeze" checklist.

- I don't think it can be some issue related to Ubuntu using the partition that Windows is on because the login screen appears the first time, so it's accessing the drive. It appears to be while loading something in the background after it has pretended that it fully rebooted that it dies.

I can't understand the connection between having previously run Ubuntu and a delayed login freeze up in Windows 10, but there it is. If anyone has a clue I'd be thankful.

---

### Post by dvdbillen on 2016-09-24
It's been a long time, but in case anyone ever has the same problem, here's what it was:

I traced the crash to the NIC driver and determined it was NoMachine. I was using it to access the desktop of a MacBook, (which is always there on the network 24/7 when I am in town). Without using it the problem goes away.

I can only speculate the reason. Somehow if NoMachine on the OSX device established communication with NoMachine on Ubuntu then the next time I booted Windows, (even much later), and the NIC driver started up with the same MAC... crash. Then reboot Windows to try again and it would work.

---

