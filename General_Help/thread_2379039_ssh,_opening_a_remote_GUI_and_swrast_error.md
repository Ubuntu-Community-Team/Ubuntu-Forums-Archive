---
title: "ssh, opening a remote GUI and swrast error"
date: 2017-11-30
forum: General Help
---

### Post by jrglez on 2017-11-30
I am trying to run a software with a GUI on a server via ssh -Y. The graphical window opens, but it freezes immediately and the following error message appears in the terminal: 
```
libGL: screen 0 does not appear to be DRI2 capable[INDENT]libGL: OpenDriver: trying /usr/lib64/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib64/dri/swrast_dri.so
libGL: Can't open configuration file /ddn/home/vtcb83/.drirc: No such file or directory.
libGL: Can't open configuration file /ddn/home/vtcb83/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error: BadValue (integer parameter out of range for operation) 2
  Extension:    154 (Uknown extension)
  Minor opcode: 3 (Unknown request)
  Resource id:  0x0[/INDENT]

```My local machine has Ubuntu 14.04,with a NVIDIA GeForce GTX 960, and I am using the latest version of the NVIDIA drivers.
I think it has to do with my local machine, because when I change to X.org drivers, it works fine. 
I have tried [this]("https://askubuntu.com/questions/451221/how-do-i-install-the-nvidia-driver-for-a-geforce-gt-630/451248#451248") and [this]("https://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update"), but it did not fix it. 


Best wishes, 
Juan

---

### Post by SeijiSensei on 2017-11-30
Have you run "sudo nvidia-xconfig" to create an xorg.conf to match the NVIDIA card?

---

### Post by jrglez on 2017-12-01
Yes, I did, but that only saves the current configuration, doesn't it?
Thanks!

---

