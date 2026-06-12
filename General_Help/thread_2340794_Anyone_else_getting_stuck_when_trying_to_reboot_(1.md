---
title: "Anyone else getting stuck when trying to reboot (14.04)?"
date: 2016-10-22
forum: General Help
---

### Post by saltydingo on 2016-10-22
It's not often I see a thread of people with my exact issue and no resolution: [https://ubuntuforums.org/showthread.php?t=2218590](https://ubuntuforums.org/showthread.php?t=2218590)

I wanted to to add a 'me too' to this thread, but it was closed. I've tried all the grub options and it still hangs after saying 'restart with rpcbind -w'. No helpful messages on screen or in syslog. Periodic hdd activity blips, so it looks like it's trying to stop something, it just won't tell me what. 

Running 14.04 on an x64 Atom. Tried everything in the linked thread except reinstalling.

---

### Post by saltydingo on 2016-10-28
Finally solved. Something was wrong with my bluetooth service. Easy to see with 'stop bluetooth' or 'start bluetooth'. What made it really hard was that it gave no error, just hung with no output, so no log files could show it. The only reason I found it at all was by looking at 'ps -aux' while a bluetooth package was stuck during a preinst script. There I could see the command the install script was trying to execute. For users of bluez who also get this issue: ppa-purge to get back to vanilla, reboot, test you can start and stop bluetooth, then install bluez and test again.

---

