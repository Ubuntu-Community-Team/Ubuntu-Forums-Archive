---
title: "apt-get upgrade borked remote box"
date: 2007-04-28
forum: General Help
---

### Post by MickKi on 2007-04-28
Hi All,

First post ever!  :)

A friend asked me to update/upgrade his machine (an old laptop with Ubuntu server on it).  I ssh-ed into it and ran apt-get update and then apt-get upgrade.  I had to download and update some debian gpg keys in the process, but thought that all went well - other than some complaint about /bin/grub-config.  It seemed that this was more of a warning rather than a critical error.

Eventually, I decided to reboot and that was that.  The machine will not reboot - my friend texted me that it says it cannot find /dev/hda1.

I asked him to use the LiveCD to get to a command prompt and run /etc/init.d/sshd start to allow me to get to the machine and try to troubleshoot it.  It came back with an error: waiting to mount root fs (or something similar).

I thought that apt-update/upgrade are pretty innocuous commands but this one has left us in the lurch.  Can you please help me recover this little server?
-- 
Regards,
Mick

---

### Post by MickKi on 2007-04-28
Hey!  Second post ever!  :)

My friend sent me the exact error:```
ALERT!  /dev/hda1 does not exist.  Dropping to a shell!!

BusyBox version 1.1.3

(initramfs)
```This most likely means that the grub/menu.lst was not autoconfigured correctly?  Any ideas?

---

### Post by MickKi on 2007-04-29
Bump!

Any ideas - could it be the libata change in the kernel (2.6.17-10-server) messing up /etc/fstab for / ?

-- 
Regards,
Mick

---

