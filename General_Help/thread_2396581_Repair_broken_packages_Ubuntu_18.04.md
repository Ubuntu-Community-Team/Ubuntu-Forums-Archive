---
title: "Repair broken packages? Ubuntu 18.04"
date: 2018-07-18
forum: General Help
---

### Post by janne-peltonen on 2018-07-18
While trying to install ndiswrapper from the official repo's, it got stuck at a part "generating 2048 bit RSA key", and I aborted the installer. Now it says I need to run dpkg --configure -a, but that gets stuck forever too at the last part (see copy paste from terminal). I did try deleting segments relating to ndiswrapper on dpkg status file, but that did no good. 

Any ideas how to start fixing this, or is it time for a reinstall?

```
janne@janne-ThinkPad-T480:~$ sudo dpkg --configure -a
Setting up ndiswrapper-dkms (1.60-6) ...
Removing old ndiswrapper-1.60 DKMS files...

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.60
Kernel:  4.15.0-23-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-23-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.60
completely from the DKMS tree.
------------------------------
Done.
Loading new ndiswrapper-1.60 DKMS files...
Building for 4.15.0-23-generic
Building initial module for 4.15.0-23-generic

```

---

### Post by kc1di on 2018-07-18
try this ```
sudo apt purge ndiswrapper
``` Then this ```
sudo apt autoclean
``` see if that works. 
if it does you can try reinstalling ndiswrapper. good luck.

---

### Post by janne-peltonen on 2018-07-18
Hi, thanks for your message. However, any apt operation currently results into the nag about dpkg being interrupted. 

```
janne@janne-ThinkPad-T480:~$ sudo apt purge ndiswrapper
[sudo] password for janne: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by kc1di on 2018-07-18
ok you can go to /var/lib/dpkg/stutus file and open as root with gedit and delete the ndiswrapper file and save the file.
Then re run```
dpkg --configue -a 
``` 
you can try this first though see if it works: ```
sudo dpkg --purge ndiswrapper
```

---

