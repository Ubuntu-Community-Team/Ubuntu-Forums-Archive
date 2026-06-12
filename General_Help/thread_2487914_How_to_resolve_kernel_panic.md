---
title: "How to resolve kernel panic"
date: 2023-06-18
forum: General Help
---

### Post by tc2020 on 2023-06-18
Hello all,

I have a headless system based on Raspberry Pi 4B running Ubuntu Server 64-bit 22.04 LTS and 5.15.0-1030-raspi kernel.

From  time to time, I get a kernel panic event ("Kernel panic - not syncing: Attempted to kill init!") after I enter "sudo reboot"  command. When this happens, the system is stuck.  The only way to recover it (as I know of) is to do a physical reset or  cycle power. Having said that, I can do many "sudo reboot" in a row  without having this kernel panic. In this system I use Log2RAM to  redirect /var/log to RAM. I also use logrotate, remove log archives, and  truncate log files.

Questions:

1). What seems to be the cause of this event?. Would Log2RAM or log removal lead this this event?.
2). Is there a way to recover it without a physical reset, as this system is for unattended use?.
3). What precautions to take to avoid this problem?.

Any help/hints would be very much appreciated. Thanks.

---

