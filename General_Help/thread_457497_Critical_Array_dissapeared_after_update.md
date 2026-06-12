---
title: "*Critical* Array dissapeared after update"
date: 2007-05-28
forum: General Help
---

### Post by PsYcHo_SiB on 2007-05-28
I just updated my webserver to the latest Ubuntu 7.04 distro and when I rebooted my software raid array dissapeared.

If I remember correctly I used mdadm to create the array in /dev/md0. But when I list in dev, md0 is nowhere to be found. I need to rebuild the array but I don't know how.

I had 5 devices in that raid array:
/dev/hdc
/dev/hde
/dev/hdf
/dev/hdg
/dev/hdh

My array was built in linear-mode (one big "hard-drive"). So I would like to know how will I rebuild my array without losing any data on those hard-drives ?

Thank You

---

### Post by PsYcHo_SiB on 2007-05-28
WOW.

I just rebooted the server and the array popped up !

I'm one lucky boy :p

---

### Post by PsYcHo_SiB on 2007-05-28
Weird. If I reboot my computer sometimes the /dev/md0 shows up and then it dissapear. 

I type this command in: sudo mknod -m 0660 /dev/md0 b 9 0
and after the array shows up. I reboot and it dissapear.

What is wrong with that ?

---

### Post by PsYcHo_SiB on 2007-05-28
Looks like and issue with udev

A bug as been filled:
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/102933]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/102933")

---

