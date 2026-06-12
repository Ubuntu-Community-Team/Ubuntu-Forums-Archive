---
title: "Upgrade problem"
date: 2006-08-17
forum: General Help
---

### Post by satimis on 2006-08-17
Hi folks,

Ubuntu-6.06-i386

While running "apt-get upgrade". Firefox crashed making the PC hanging.  After pressing force-reset to reboot PC, I can't run "apt-get upgrade"

$ sudo apt-get upgrade```

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Running "sudo dpkg --configure -a" and "sudo apt-get update" did not help.  Please advise how to fix the problem.  TIA

B.R.
satimis

---

### Post by DoctorMO on 2006-08-17
it's recomended that you quit all applications that will be upgraded... although most of the time it will still work.

have you tried sudo apt-get dist-upgrade?

---

### Post by givré on 2006-08-17
Which version of the kernel do you actually run (uname -r in a terminal)

---

### Post by satimis on 2006-08-17
Hi DoctorMO,

I got it fixed by running "sudo apt-get dist-upgrade"

Tks.

B.R.
satimis

---

### Post by satimis on 2006-08-17
Hi givré,

$ sudo uname -r```

Password:
2.6.15-23-386
```

Tks.

B.R.
satimis

---

