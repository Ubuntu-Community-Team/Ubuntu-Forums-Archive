---
title: "Ubuntu on vmware player for Windows time problem"
date: 2007-03-12
forum: General Help
---

### Post by djensen47 on 2007-03-12
I'm using VMWare Player for Windows to run Ubuntu Desktop 6.06. 

Everything on the Ubuntu desktop works fine accept for the time of day on the clock. The time seems to be running exactly double fast. After 4 minutes of real time 8 minutes will have passed.

I found some posts about issues with AMD 64 or certain motherboards but I couldn't find any solution with regard to this issue on VMWare.

Has anybody else experienced this problem? Any solutions?

Thanks.

---

### Post by djensen47 on 2007-03-12
I only noticed this yesterday. Maybe it is coincidence but could it be related to the new daylight savings?

---

### Post by DerHesse on 2007-03-12
You need vmware-tools installed on the guest, after the vm was set up.
If already installed, then check the box "time synchronization with the host".


If it is not installed It cannot be done with the vmware-player. To install the tools you do need vmware-server (freeware)  or vmware-workstation.

---

### Post by djensen47 on 2007-03-12
Sorry for my ignorance but I think I need a little more specificity. 

What are vmware-tools? By guest I assume you mean the machine running in the VMWare player? In this case the guest would be Ubuntu? Or do you mean the opposite? 

If I have vmware-tools, where do I find this checkbox?

I downloaded the Ubuntu 6.06 Desktop vm from the VMWare website directly. 

> **DerHesse said:**
> You need vmware-tools installed on the guest, after the vm was set up.
If already installed, then check the box "time synchronization with the host".


If it is not installed It cannot be done with the vmware-player. To install the tools you do need vmware-server (freeware)  or vmware-workstation.

---

### Post by djensen47 on 2007-03-12
Here are some of the answers to my own questions ...

[https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

---

### Post by Fatjoint on 2007-03-13
Why can't you use the ntp-daemon to keep time right?  Is this machine not connected to the internet?

---

