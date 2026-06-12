---
title: "VMware: ubuntu host slower than 2003 server host!"
date: 2007-05-29
forum: General Help
---

### Post by brandilton on 2007-05-29
I'm fairly new to VMware and linux and here's where I'm stuck.

My first venture into vmware was to install VM server on a win2003 host. I created 2 2003 server guests and all was good except that I did not like the dependence of the 2 guests on the 2003 host (which does get frequent reboots).

my solution was to virtualize the 2003 host (using converter) and install ubuntu as the new host with the 3 2003 servers as guests. The process went well and everything works, however all servers are significantly slower than the first scenario. all 3 guests act like they have very little RAM (everything slow to open, etc.)

hardware specs:
Pentium D 2.8GHz (a dual core chip)
3GB RAM
Adaptec 2420 256MB RAID 1 with 2 10K RPM drives

guest settings:
guest 1 (most important, and running slowest, was converted): 1 processor, 2636MB RAM, non pre-allocated drives
guest 2: 1 processor, 1024 RAM, non pre-allocated drives
guest 3: 1 processor, 1024 RAM, non pre-allocated drives

One thing that puzzles me is that when i open system>applications>system monitor on the host, it shows that memory and swap history is cumulatively using less that 10%. The icon that shows RAM usage shows 11% used by programs 88% used by cache.

I can't figure out what is causing all 3 guests to run so slowly when they ran much faster on the same hardware with win2003 as the host.

here's my free -m report if that helps:
total used free shared buffers cached
Mem: 3043 2921 121 0 17 2670
-/+ buffers/cache: 233 2809
Swap: 8911 129 8781


why is ubuntu not allocating RAM to these virtual machines?

---

### Post by ikonia on 2007-05-29
1.) your running a different config on ubuntu than you are on windows.

you windows config was 1 native OS and 2 guest OS's, your ubuntu config is 1 native host os and 3 VM guest os's when your using 2 GB of ram for 2 VM's that only leaves 1 GB of ram for your third vm AND your host OS.

I suggest that is where your issues are.

---

### Post by brandilton on 2007-05-29
right, but the additional OS is ubuntu which is stripped to nothing but vmware server running.  it's barely using any resources. 

Even if i turn off 2 of the 3 VMs so that it's running ubuntu and 1 2003 server, that 2003 server is slower than when it was the host and had 2 other 2003 VMs running on it...

---

