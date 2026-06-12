---
title: "Ubuntu 18.04.2 LTS won't boot without monitor + VNC issue?"
date: 2019-05-07
forum: General Help
---

### Post by aidangraf on 2019-05-07
Currently running Ubuntu 18.04.2 LTS on multiple old Lenovo ThinkCentre M78 desktops. On machine startup, if there is a monitor plugged in, the OS boots just fine. If there is no monitor plugged in however, it starts up but remains at a black screen. This is seen when plugging in the monitor after giving it a good couple minutes of boot time without one. I don't want to jump to conclusions and say that the OS isn't booting, as I can successfully remote in to the PC via VNC (which was configured to automatically run on startup). However, when remoting in via VNC, the VNC connection being displayed is just a black screen. I don't think this is a BIOS issue, as nowhere in the machine's BIOS is there anything about requiring a monitor to boot, and I'm assuming the OS is in fact booting, seeing as I can establish a successful VNC connection. I would rather not use a dummy display driver as I would like to still be able to view the display output when a VGA cable is connected. If any specifics are needed about the hardware or software I would be willing to provide whatever is necessary. Any help would be much appreciated!

---

### Post by TheFu on 2019-05-07
Can you ssh in? This assumes that openssh-server is installed an working, of course.  If the machine is internet-facing, be certain to lock it down AND take proactive protections against attacks, like not using passwords, ever. Always use keys, never passwords.  sshd_config has settings to only allow passwords on specific LANs, but require keys everywhere else.

VNC really shouldn't be used without a VPN or ssh tunnel. It isn't secure.  There are thousands of VNC connections hacked daily.

---

