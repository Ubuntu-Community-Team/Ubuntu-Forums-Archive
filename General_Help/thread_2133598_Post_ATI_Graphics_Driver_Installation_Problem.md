---
title: "Post ATI Graphics Driver Installation Problem"
date: 2013-04-08
forum: General Help
---

### Post by javadecoder on 2013-04-08
Hi, 

I have a g6 Pavilion HP laptop with 4 GB RAM & 1GB Graphics Card ATI Radeon HD 6470M . I recently installed ubuntu 12.04 LTS 32 Bit version , and since it caused a lot of heating I also installed the appropiate ATI drivers from their website which included catalyst control centre. After succesful installation everything was working quite smooth with normal CPU temperatures and 'fglrxinfo' gave all correct results . But when I switched to Intel Integrated Graphics Card and then rebooted the system , Unity interface failed to load and now whatever graphics related command I try I get the following result : 

```
piyush@Piyush:~$ sudo amdcccle
amdcccle: error while loading shared libraries: /usr/lib/libGL.so.1: file too short
```

To get a workaround the situation , I installed gnome-shell and atleast it is now a bit alright.But I can't access the catalyst control centre , and any graphics related options . Also I faced another side problem , which is stucking of ubuntu at the shut down process. It is never able to shut down properly after that reboot which caused Intel Graphics Card to come into action . (The shutdown screen stays at the screen containing ubuntu dots.)

Somebody please tell me what steps to take now except reinstallation of Ubuntu itself :confused:

---

