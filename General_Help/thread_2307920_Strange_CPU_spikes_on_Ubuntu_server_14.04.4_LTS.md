---
title: "Strange CPU spikes on Ubuntu server 14.04.4 LTS"
date: 2015-12-29
forum: General Help
---

### Post by richieb2 on 2015-12-29
Hi Ubuntu folks!

I was wondering if you can help me on this issue. Basically we are having random CPU spikes, not sure of the duration, but we want to find out what process(es) is causing these random spikes. I was wondering if there is a tool or script that can be run to let's say, any process(es) that are using 50% or more of the CPU to pipe to tell me which process or processes are the culprit.

The development team is blaming the Hyper-V infrastructure (where this particular VM is hosted Hyper-V Server 2012 R2) but I highly doubt that is the problem, unless anyone knows of any issues related to Hyper-V and linux guests. 

Any ideas on how to approach this?

TIA

---

### Post by bab1 on 2015-12-30
> **richieb2 said:**
> Hi Ubuntu folks!

I was wondering if you can help me on this issue. Basically we are having random CPU spikes, not sure of the duration, but we want to find out what process(es) is causing these random spikes. I was wondering if there is a tool or script that can be run to let's say, any process(es) that are using 50% or more of the CPU to pipe to tell me which process or processes are the culprit.

The development team is blaming the Hyper-V infrastructure (where this particular VM is hosted Hyper-V Server 2012 R2) but I highly doubt that is the problem, unless anyone knows of any issues related to Hyper-V and linux guests. 

Any ideas on how to approach this?

TIA
From the terminal you can use the tool ***top *** or the enhanced tool ***htop***.  Htop is not installed by default so you need to run ```
sudo apt-get install htop
```...for it to be available.

---

