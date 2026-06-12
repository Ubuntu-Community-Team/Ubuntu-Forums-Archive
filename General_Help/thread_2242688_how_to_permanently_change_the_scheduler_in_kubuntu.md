---
title: "how to permanently change the scheduler in kubuntu 14.04"
date: 2014-09-03
forum: General Help
---

### Post by macstar on 2014-09-03
hi guys, i ran into  a problem.
how to permanently change the scheduler in kubuntu 14.04?

i tried the following already:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop
in my /etc/default/grub

after that sudo update-grub2.
reboot. 
scheduler remains on deadline.

next try:
block/sda/queue/scheduler = noop

in 
etc/sysfs.conf

again updated grub2, reboot.
nothing: scheduler remains on deadline.

if however i do it by:
echo noop > /sys/block/sda/queue/scheduler

it switches to noop, obviously only as long as i use the system, and get's back to deadline after a reboot.


so my question is:
how can i change the scheduler permanently?

---

### Post by cariboo on 2014-09-03
Moved to General Help.

---

