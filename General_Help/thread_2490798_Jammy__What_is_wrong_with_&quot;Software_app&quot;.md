---
title: "Jammy : What is wrong with &quot;Software app&quot; ?"
date: 2023-09-16
forum: General Help
---

### Post by georgesgiralt on 2023-09-16
Hello, I'm very ew with this ap. It did ot exist in the previous LTS version I was using, so I'm very very surprised by it's behaviour. 
Last day I had a pop up stating that a system update was pending and that  a restart was mandatory.
I said yes (I'm a bit of an experimenter). And I saw the laptop restart TWICE ! Afterwards I checked what was installed. It was thermald daemon package !
Are you kidding ? A restart of the whole system for a simple and so straightforward tool ? And twice ? 
Today, same question about system install and restart necessary. Upon checking, these are : 
```

libnss-systemd libpam-systemd libsystemd-dev libsystemd0 libudev1 systemd systemd-oomd systemd-sysv systemd-timesyncd udev

``` 
Nothing absolutely necessary and, IMHO, nothing requesting a reboot. 
Last and most important, apt report these updates as "timely" : 
```

# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libnss-systemd libpam-systemd libsystemd-dev libsystemd0 libudev1 systemd systemd-oomd systemd-sysv systemd-timesyncd udev
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

```
So how come that Software want to install them NOW and restart my computer ? 
Thanks a lot in advance for your help ! 
Have a nice and bright day !

---

### Post by TheFu on 2023-09-16
systemd is a core part of the OS, unfortunately.  Some of the things it reads only are read at boot time, so getting any config changes for those core parts requires a reboot.  I don't know why there would be two reboots, unless there was some file system corruption problem.

Of a kernel module needs to be reloaded after an upgrade, that would be accomplished by a reboot.  There are manual ways to unload the kernel-module, then reload a new one, but I've never noticed that being done.

I'm patching my systems now.  Saturday morning is when I patch them.  I see libc-bin libc6 are being updated. These ARE core libraries and a reboot (on that system) will be necessary.  Basically, **_*all software on the system is dependent on libc*_**, so it make sense to require a reboot. Short of the kernel with a critical remote access security bug, nothing is higher priority than libc.  Things will start breaking, quickly, if I don't reboot that system.

I see another system is getting libc, libsystemd0, ssh, and some security updates too.  I suspect there is a critical security bug that is being corrected before being announced.  

Some more systems being patched ... a few claim to need reboots, but not all of them.  Looks like older kernels don't have the issue, whatever it is.  Ok, patching finished. Let's see who many systems need to be rebooted.    4 need to be rebooted out of 15 systems.  I don't see an obvious reason why, though 3 of those 4 systems are on 22.04.  Another 22.04-based system doesn't need a reboot. 2 run wireguard VPN servers and little else.  The 3rd is a pihole (DNS filter and LAN DNS).  So all of those have been rebooted. Just this workstation if left, which means I need to post this, then reboot it. ;)

Because I use CLI tools for patching, it is my choice to reboot now or not.  Sometimes firefox will refuse to POST or GET until it is restarted, so I will reboot more quickly when that happens.  For example, I needed to reboot this system last week, but never got around to it.  It still needs that reboot and probably one for today.


Update ... I'm back ... haven't rebooted this workstation yet. Both of my pi-hold systems aren't working, which means no DNS for the LAN.  I need to fix that ASAP for many reasons.  Appears related to IPv6 support ... which has been a problem with the pihole a few times before.

Update2:  Fixed the piholes.  They have a "repair" option in the setup-reconfigure that got everything working again ... at least everything seems to be working, so far.

---

