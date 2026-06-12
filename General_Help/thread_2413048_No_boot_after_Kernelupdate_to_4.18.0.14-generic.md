---
title: "No boot after Kernelupdate to 4.18.0.14-generic"
date: 2019-02-20
forum: General Help
---

### Post by l4schi on 2019-02-20
Hello everyone,

maybe someone can help me.
After i updated my Ubuntu 18.10 with apt upgrade i got the Kernel 4.18.0.14.
My system is crypted by LUKS by installation wizard. The crypted partition is SDA5_crypted.

Now when i start my system i get the message
```

Warning: Failed to connect to lvmetad. Falling back to device scanning.
Volume group "ubuntu-vg" not found
Cannot process volume group ubuntu-vg
Gave up waiting for suspend/resume device
Gave up waiting for root file system device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/ubuntu--vg-root dows not exist. Dropping to a shell!

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu4) built-in shell (ash)
(initramfs)

```

When i start the with Kernelversion 4.18.0.13-generic everything works fine.

Has anyone an idea?

THX

---

### Post by deadflowr on 2019-02-20
Skip it and an update should bring in the newer -15 kernel.
-14 was problematic when it was built and was the primary reason the 18.04.2 point release was delayed:
[https://community.ubuntu.com/t/ubuntu-18-04-2-testing-really-ready/9704]("https://community.ubuntu.com/t/ubuntu-18-04-2-testing-really-ready/9704")
Not sure you have the same bug, but still...

Install the updates from the bootable -13 session.

---

### Post by l4schi on 2019-02-20
> **deadflowr said:**
> Skip it and an update should bring in the newer -15 kernel.

Thanks for input. But on the newer -15 kernel i have exactly the same problem. I thought it too, that it could be a bug with 14.

Regards

---

