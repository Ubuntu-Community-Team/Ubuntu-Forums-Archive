---
title: "Do you have Intel/AMD microcode installed?"
date: 2013-08-21
forum: General Help
---

### Post by mikewhatever on 2013-08-21
Just wondering..., I've seen [bug 1212497]("https://bugs.launchpad.net/intel/+bug/1212497"), and didn't quite know what to make of it at first.
You can check with the following commands:
```

dpkg -l | grep microcode

lsmod | grep microcode
```
The 'intel-microcode' package is not part of the defalt installation, and I've never heard about it before today, yet, high priority security updates are released for it.
Having installed the package, I got this in 'dmesg'
```

[75689.129540] microcode: CPU0 sig=0x6f6, pf=0x20, revision=0xc7
[75689.133615] microcode: CPU1 sig=0x6f6, pf=0x20, revision=0xc7
[75689.136636] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[75689.198188] microcode: CPU0 updated to revision 0xd1, date = 2010-10-01
[75689.198683] microcode: CPU1 updated to revision 0xd1, date = 2010-10-01

```

The CPU is a 2006 Intel's Core2Duo.
Apparently, there is also 'amd64-microcode' in the repositories.

---

### Post by rai_shu2 on 2013-08-21
CPU firmware. Looks multiverse from what I can see:

[https://launchpad.net/ubuntu/+source/intel-microcode](https://launchpad.net/ubuntu/+source/intel-microcode)
[https://launchpad.net/ubuntu/+source/amd64-microcode](https://launchpad.net/ubuntu/+source/amd64-microcode)

---

