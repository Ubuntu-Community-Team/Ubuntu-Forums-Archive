---
title: "computer slow after wake up"
date: 2017-04-24
forum: General Help
---

### Post by cost3 on 2017-04-24
After suspending and waking up, my laptop is always very slow. I have already googled about it and tried to install msr-tools and set the msr register to 0 but got error messages.

Any other solutions? Thats what I get in the terminal. OS: Ubuntu 16.04 LTS

```
sudo apt-get install msr-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msr-tools is already the newest version (1.3-2).
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
sudo modprobe msr
sudo rdmsr -a 0x19a
rdmsr: CPU 0 cannot read MSR 0x0000019a
sudo wrmsr -a 0x19a 0x0
wrmsr: CPU 0 cannot set MSR 0x0000019a to 0x0000000000000000
```

---

