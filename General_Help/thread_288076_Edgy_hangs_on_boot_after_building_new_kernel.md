---
title: "Edgy hangs on boot after building new kernel"
date: 2006-10-29
forum: General Help
---

### Post by dik666 on 2006-10-29
Hi,

I'm having a boot problem with Edgy while trying to build my raid 5 server.

I did a fresh install of Edgy and then rebuilt the kernel using the directions at "http://doc.gwos.org/index.php/Kernel_Compilation_Dapper" in order to use my RocketRaid 1640 card.  The only change I made was disabling the HPT36X support.

I then rebooted the machine and everything worked.  I installed "mdadm" using APT-GET and then rebooted.  This time the system hung during reboot.  If I go back and uninstall mdadm the system will boot ok again.

I tried following the workaround at "https://launchpad.net/distros/ubuntu...ols/+bug/67256" in case my problem was similar but it did not work.

Any thoughts?

Thanks,
dik666

---

