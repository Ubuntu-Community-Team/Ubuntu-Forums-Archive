---
title: "Ubuntu Hyper-V Live Backups"
date: 2017-11-06
forum: General Help
---

### Post by ryan152 on 2017-11-06
Hey everyone, I've got a interesting question and issue here. I've setup an Ubuntu Server 14.04 as a guest under Windows 2008r2 hyper-v server. I'm struggling getting VSS daemon woking so I can perform live backups. As a test, I installed a new 16.04 server and again the issue is the same. I've used the documentation here, [https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v](https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v).

Basically both guest installs experience the same issue, 14.04 and 16.04

Hyper-V VSS: VSS starting; pid is:845
Hyper-V VSS: open /dev/vmbus/hv_vss failed; error: 2 No such file or directory

Hyper-V VSS: open /dev/vmbus/hv_vss failed; error: 2 No such file or directory

The only module I see in that directory is hv_kvp

One think to note is that the file copy daemon is the same issue

HV_FCOPY: starting; pid is:855
HV_FCOPY: open /dev/vmbus/hv_fcopy failed; error: 2 No such file or directory

---

### Post by btindie on 2017-11-08
According to that doc you linked to, *Live virtual machine backup* is only supported on 2016 / 2012 R2

---

