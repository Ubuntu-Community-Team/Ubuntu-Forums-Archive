---
title: "Ubuntu Mate 20.04, xbox.drv, no rc.local"
date: 2022-11-19
forum: General Help
---

### Post by SciGuy1872 on 2022-11-19
Hi.  My xbox controller won't work for games outside Steam unless I run: sudo xboxdrv --detach-kernel-driver.  I found that I just need to edit a file in /etc/rc.local, as that file runs with root permission at startup.  Requiring root, just adding to Startup Programs is not going to work.  I have provided a screenshot that shows that I have no rc.local file and another screenshot that shows that there are two service files that relate to rc.local.  I checked the cron files, but haven't had luck editing for startup options; there are screenshots of those files, too.

---

### Post by TheFu on 2022-11-20
I know nothing about xbox-anything and don't game on Linux ... but 

If you don't have a file and need it, then create it. Be certain to get the permissions (execute) set correctly or it won't work.
Also, rc.local is deprecated. We are supposed to create systemd "unit files" as replacements. There are 50+ unit file examples on your system already and thousands on the internet.

However, drivers are normally loaded using settings in /etc/modprobe.d/.  Those are all text files. Take a look and you'll figure out the way they work. Probably don't need to look at the blacklist files, just the other files that install drivers into the kernel.  I'm assuming the driver is a real kernel driver, not something being called a driver that is really a specialized program ... like some touchpads have.

---

