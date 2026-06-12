---
title: "libgpu.so? epsxe plugin"
date: 2006-12-17
forum: General Help
---

### Post by Tekovro on 2006-12-17
plugins/libgpu.so: cannot open shared object file: No such file or directorytekovro@tekovro-desktop:~$ 

i have a epsxe and im pretty sure i set it up properly but when i go to run cdrom the terminal gives me that response and closes epsxe.

i checked in my plugin folder and i did not see any libgpu.so file. 

so then i checked my video plugin and tried changing it to a different one. tested it and it said everything was ok, I tried it again and i got the same message.

---

### Post by yangyuruc on 2008-02-28
enter plugins
copy libgpuPeteXGL2.so.2.0.8 
and name libgpuPeteXGL2.so.2.0.8 's replicate as libgpu.so

yangyu@yangyu-desktop:/media/sda5/ubuntu&#65293;soft/epsxe160lin/plugins$ cp libgpuPeteXGL2.so.2.0.8 libgpu.so

---

