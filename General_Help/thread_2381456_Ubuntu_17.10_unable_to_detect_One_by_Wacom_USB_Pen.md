---
title: "Ubuntu 17.10 unable to detect One by Wacom USB Pen Tablet Model CTL-472"
date: 2017-12-31
forum: General Help
---

### Post by alisaeedrana on 2017-12-31
I am unable to detect One by Wacom USB Pen Tablet on Ubuntu 17.10.

[ATTACH=CONFIG]277984[/ATTACH]

One by Wacom
Pen Tablet Model: CTL-472

I get the following error:

```

dmesg | grep -i wacom
[    1.327960] usb 1-2: Manufacturer: Wacom Co.,Ltd.
[    1.335540] wacom: loading out-of-tree module taints kernel.
[    1.335540] wacom: loading out-of-tree module taints kernel.
[    1.335570] wacom: module verification failed: signature and/or required key missing - tainting kernel
[    1.335867] wacom: probe of 0003:056A:037A.0001 failed with error -22
[    1.335883] wacom 0003:056A:037A.0002: Unknown device_type for 'Wacom Co.,Ltd. CTL-472'. Ignoring.
[   34.830016] usb 1-2: Manufacturer: Wacom Co.,Ltd.
[   34.836193] wacom: probe of 0003:056A:037A.0007 failed with error -22
[   34.838045] wacom 0003:056A:037A.0008: Unknown device_type for 'Wacom Co.,Ltd. CTL-472'. Ignoring.

```

My system is:

```

uname -a
Linux ali-ubuntu 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

I have tried the following guide:

[https://wiki.archlinux.org/index.php/Wacom_tablet#USB-devices](https://wiki.archlinux.org/index.php/Wacom_tablet#USB-devices)



Please help.

---

### Post by virgosun on 2017-12-31
[#6]("https://ubuntuforums.org/showthread.php?t=2360855&p=13716537#post13716537")

---

### Post by alisaeedrana on 2018-01-02
> **virgosun said:**
> [#6]("https://ubuntuforums.org/showthread.php?t=2360855&p=13716537#post13716537")

Hi, thank you for your reply. I've tried these instructions line by line but still not working. 
Anything else I can try?

---

### Post by uttampal on 2018-03-09
I am having the exact same problem.

---

### Post by oldos2er on 2018-03-09
uttampal, please start your own support thread if you're seeking an answer to this problem, thanks.

---

### Post by wildmanne39 on 2018-03-09
Hello uttampal, if you need help please start your own thread as it gets confusing having more then one person being helped in the same thread.

Thanks

---

