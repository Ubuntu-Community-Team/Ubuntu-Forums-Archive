---
title: "network interface"
date: 2008-01-02
forum: General Help
---

### Post by odo298 on 2008-01-02
I just installed ubuntu and it will not see the nvidia network card. Thus I cannot get online unless I load my windows os (yuk!).The live cd doesnt see it either. If there is a special driver pakage out there, I could use some help! I am fairly new to linux but I really like the whole open source thing. I also tried kubuntu because I am used to the kde desktop, and I had the same trouble! Anyone?

odo298

---

### Post by PeterJS on 2008-01-02
Is it a built in NIC on an nForce motherboard? That's the only "nvidia" network card I can think of. Could you post the output of lspci for us?

This documentation might be a start in the right direction:
[https://help.ubuntu.com/community/NvNetInstallation](https://help.ubuntu.com/community/NvNetInstallation)
It's pretty old, hopefull somebody with some more recent experience will find this thread.

---

### Post by p_quarles on 2008-01-02
Let's see if it recognizes the card. Open a terminal, type the following, and post the output here:
```
ifconfig -a
```

---

