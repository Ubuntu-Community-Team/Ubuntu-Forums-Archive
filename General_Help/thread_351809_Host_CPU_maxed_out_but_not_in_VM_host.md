---
title: "Host CPU maxed out but not in VM host"
date: 2007-02-02
forum: General Help
---

### Post by lecrucious on 2007-02-02
I have set up an HP DL 360 with 4GB of RAM and (2) 2.84 GHz Xeons. The host OS is ubuntu 6.10 server. Kernel version is 2.6.17-10-server. I have one VM running with a single processor assigned and 512MB of RAM. The VM is a Ghost image from a physical machine, how I got it to work is for another discussion. It runs fine. Here's my problem. When looking at the host via "top" the one "vmware-vmx" uses 101 - 111% of processor while inside the VM via task manager it peaks at 2%. I can't explain this and don't know where to start looking. I have four other hosts running suse 10.0 without this problem.

---

