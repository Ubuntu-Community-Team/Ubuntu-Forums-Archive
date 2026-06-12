---
title: "bootlogd not working"
date: 2008-06-22
forum: General Help
---

### Post by Pollywoggy on 2008-06-22
I upgraded this morning to kernel 2.6.24-19 (Hardy) but when I rebooted the machine, I got some error that began with a UUID and ended with "Booting normally".  I want to log this error and I have 

BOOTLOGD_ENABLE=yes

in /etc/default/bootlogd


But it is not logging anything.  Since the error happens at the beginning of the boot, dmesg does not show anything wrong.  The machine does finish booting but something seems to be wrong or there would not be this error message.

---

