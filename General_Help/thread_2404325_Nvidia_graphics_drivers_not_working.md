---
title: "Nvidia graphics drivers not working"
date: 2018-10-22
forum: General Help
---

### Post by romanze on 2018-10-22
Hello all new Linux user here. I have been googling the last 3 days trying to solve this myself. 
I've had issues with my Nvidia graphics drivers since I first installed Ubuntu 18.04. 
I received errors like "Failed to start load kernel modules", "pkcs#7 signature not signed with a trusted
key", and some gnome desktop errors, could be unrelated. I'm at the point now where i tried installing the.run driver from
Nvidias website and it's screwing me up even more. The main problem is when i start my computer it hangs at the pkcs error and
Won't continue to boot. After 3 reboots I can get to the desktop. I purged all Nvidia drivers, but i believe the ones I installed
Manually are still there. I was going to install through the update again but the options are greyed out and it says I
Have manually installed drivers. Is it best to reinstall ubuntu at this point, or should i do something else? I really want to love Linux, 
But all I have been having are issues.

Things Ive tried: 
sudo apt-get remove nvidia*
sudo apt-get autoremove
dpkg --get-selections | grep nvidia which results in:
    libnvidia-compute-390:amd64            deinstall
    libnvidia-compute-390:i386            deinstall
    libnvidia-compute-396:amd64            deinstall
    libnvidia-compute-396:i386            deinstall
    libnvidia-compute-410:amd64            deinstall
    libnvidia-compute-410:i386            deinstall

---

### Post by oldos2er on 2018-10-22
Can you specify which Nvidia card you have? 

```
 lspci | grep VGA 
```

---

### Post by romanze on 2018-10-22
02:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1). Something else to add, all the boot problems go away when I remove nvidia drivers. I recently updated to 18.10 and I think that may be why I am getting the signature issues. Which have sparked the boot issues, but I always have nvidia driver issues. No that I hopefulyl removed the nvidia drivers I want to install new ones through Software Updater, but like I said in my first post, the options are greyed out and it says I have "Manually installed Drivers" which I am assuming are the .run drivers I installed from Nvidias website.

---

