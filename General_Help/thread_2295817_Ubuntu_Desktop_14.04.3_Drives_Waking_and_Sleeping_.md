---
title: "Ubuntu Desktop 14.04.3 Drives Waking and Sleeping Continuously"
date: 2015-09-21
forum: General Help
---

### Post by Ettore_Casagrande on 2015-09-21
I've had this Ubuntu server, basically unchanged, for a few years (upgraded to 14.04 recently).  I've never had any drive sleeping problems with it until recently, but unfortunately, I changed a bunch of things.  Server was originally a media server / file server previously, but I recently converted it into a router.

**What is happening?**
Harddrives that are not in use are going to sleep then immediately re-waking up; if I set sleep to 6 minutes, they never sleep.  If I set them to 5 minutes, they spin down and wake up immediately. If I set them to 10 seconds, then 4 minutes, 50 seconds later they wake up.
Edit: I set one drive to 10 seconds, one to 3 minutes, one to 4 minutes, and one to 6 minutes. The first 3 sleep as expected, but at 5 minutes, all 3 wake up.  The 5 minute interval is consistent (as in, it happens at 4:02, 4:07, 4:12, etc ... it has nothing to do with when the original drive went to sleep).

**What changed?**
- Reset BIOS (because I accidentally disabled the onboard videocard)
- Did all of this stuff to turn Ubuntu into a router ( [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) ) TL;DR IPTABLES stuff, DHCP, DNS, configured NICs
- Installed Webmin
- Installed an Intel dual gigabit PCI-e card

**What have I tried?**
# lsof +D /mnt/share_name (nothing comes up, but spends a few seconds accessing the drive ... changed share_name to match the share name)
# echo 1 | sudo tee /proc/sys/vm/block_dump (syslog shows a bunch of stuff for SDA, but nothing for SDB-SDE, the drives that should be staying asleep but aren't)
Unmounting the file systems.  With the file system unmounted, the same sleep-wake pattern happens as above.

**Configuration?**
Motherboard is an M4A88T-M w/X2 255 chip and 2x 2GB RAM, and all drives are in AHCI mode. Intel 520 SSD, 2x 3TB Seagates, 2x 2TB Hitachi, IDE DVD-ROM.

I don't know what else to try, but since that SYSLOG thing didn't work, I presume that means that the motherboard is waking the drives for some reason.  It's very annoying, because the system is pretty crippled while it waits to put 4 drives to sleep, then waits to fire all 4 up again.

---

