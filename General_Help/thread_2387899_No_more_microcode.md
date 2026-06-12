---
title: "No more microcode?"
date: 2018-03-25
forum: General Help
---

### Post by ubname on 2018-03-25
Hi,

hi noticed that lately no more microcode drivers are offered in Ubuntu 17.10 (same place where you can select nvidia drivers), what has changed?

4.13.0-37-generic #42-Ubuntu SMP are they already embedded with the kernel now?


thanks.

---

### Post by mc4man on 2018-03-25
Maybe this change to ubuntu-drivers-common
> * detect-plugins/cpu-microcode.py, UbuntuDrivers/detect.py:
    - Remove the cpu-microcode.py detection plugin (LP: #1738259).
      Kernel metapackages are going to have a hard dependency on the
      {intel,amd64}-microcode packages to ensure that all bare-metal installs
      benefit from microcode updates. This means that microcode packages are
      no longer "additional drivers" and since they won't be able to be removed
      without uninstalling the kernel metapackages, there is no need for them
      to be exposed by ubuntu-drivers.
 -- Alberto Milone <alberto.milone@canonical.com>  Fri, 02 Feb 2018 09:38:35 +0100

As far as the Kernel metapackages having a dep on the microcode packages haven't seen that as of yet..

According to this it^  should
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259)

However this says not, ex. xenial
> * Miscellaneous upstream changes
    - Revert "UBUNTU: Make kernel image packages depend on cpu microcode updates"

 -- Marcelo Henrique Cerri <marcelo.cerri@canonical.com>  Fri, 12 Jan 2018 16:34:13 -0200


---

### Post by Yellow Pasque on 2018-03-25
The dependency was removed at about the same time Intel announced the the spontaneous reboot problem on Haswell caused by the microcode update for Meltdown.

Either way, I'm glad they removed it from the additional driver GUI. Novice users found it confusing.

---

### Post by mc4man on 2018-03-25
> **Temüjin said:**
> The dependency was removed at about the same time Intel announced the the spontaneous reboot problem on Haswell caused by the microcode update for Meltdown.

Either way, I'm glad they removed it from the additional driver GUI. Novice users found it confusing.

Well then they should now 'unrevert' the linux-meta change. 
As far as that 'supposed' microcode issue just a few days later ubuntu released an update (3.20180108.1+really20171117.1) that would have mitigated. Actually it was the same day someone reverted the meta packages..

There is now ( as of 3/13) a new one that has supposedly been fixed in that regard - 3.20180312.0

Seems to be a lack of communication regarding the Desktop at Canonical.

---

### Post by ubname on 2018-03-25
Thanks mc4man  and Temu, i understand it is a "work in progress" so it seems "normal" to be missing.

---

### Post by Yellow Pasque on 2018-03-25
> **mc4man said:**
> Well then they should now 'unrevert' the linux-meta change.

Yeah, I agree.

---

### Post by mc4man on 2018-03-25
> **ubname said:**
> Thanks mc4man  and Temu, i understand it is a "work in progress" so it seems "normal" to be missing.
you can install the package yourself if desired, sudo apt install intel-microcode or amd64-microcode for amd.
On intel it's use can be checked via

```
/usr/sbin/iucode_tool -tb -lS /lib/firmware/intel-ucode/*
```

---

