---
title: "libGL error: failed to load driver: i965"
date: 2013-01-07
forum: General Help
---

### Post by scorpiosnake on 2013-01-07
I just upgraded to 12.10. Now when I tried to run some third party programs I get the following error:

```
libGL error: failed to load driver: i965
```

These programs were running fine under 12.04. This is Ubuntu 64 bit with Intel HD graphics.

---

### Post by brainwash on 2013-01-07
Some packages might be missing. Did the upgrade process remove any packages related to xorg/intel/mesa?

```
apt-cache policy libgl1-mesa-dri libgl1-mesa-dri:i386 | grep -C1 Installed
```

---

### Post by scorpiosnake on 2013-01-07
```
apt-cache policy libgl1-mesa-dri libgl1-mesa-dri:i386 | grep -C1 Installed
libgl1-mesa-dri:
  Installed: 9.0-0ubuntu1
  Candidate: 9.0-0ubuntu1
--
libgl1-mesa-dri:i386:
  Installed: (none)
  Candidate: 9.0-0ubuntu1

```


If I try to install libgl1-mesa-dri:i386 I get

```
The following NEW packages will be installed:
  libdrm-intel1:i386{a} libdrm-nouveau2:i386{a} libgl1-mesa-dri:i386 
  libllvm3.1:i386{ab} libpciaccess0:i386{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.6 MB of archives. After unpacking 55.1 MB will be used.
The following packages have unmet dependencies:
 libllvm3.1 : Breaks: libllvm3.1:i386 (!= 3.1-2ubuntu1irie1~precise1) but 3.1-2ubuntu1 is to be installed.
 libllvm3.1:i386 : Breaks: libllvm3.1 (!= 3.1-2ubuntu1) but 3.1-2ubuntu1irie1~precise1 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                     
1)      libgl1-mesa-dri                                                  
2)      libllvm3.1                                                       
3)      libxatracker1                                                    
4)      ubuntu-desktop                                                   
5)      xorg                                                             
6)      xserver-xorg-video-all                                           
7)      xserver-xorg-video-vmware                                        

      Leave the following dependencies unresolved:                       
8)      libgl1-mesa-glx recommends libgl1-mesa-dri (>= 7.2)              
9)      xserver-xorg recommends libgl1-mesa-dri                          
10)     xserver-xorg-video-nouveau recommends libgl1-mesa-dri (>= 7.11.1)
11)     driconf recommends libgl1-mesa-dri | xlibmesa-gl (> 6.8.0)       
12)     driconf recommends libgl1-mesa-dri | xlibmesa-dri (> 6.8.0)      
13)     xserver-xorg-core recommends libgl1-mesa-dri (>= 7.10.2-4)       
14)     xserver-xephyr recommends libgl1-mesa-dri (>= 7.1~rc1)           


Accept this solution? [Y/n/q/?]
```

---

### Post by brainwash on 2013-01-07
Some more details are needed I guess. Which applications stopped running properly? 32 bit ones? Wine related? And...
> **brainwash said:**
> Did the upgrade process remove any packages related to xorg/intel/mesa?

Looks like you won't be able to install **libgl1-mesa-dri:i386** unless you reinstall **libllvm3.1** from the official repository (currently a version from some PPA is still installed, reactivating this particular PPA might work too).

---

### Post by scorpiosnake on 2013-01-07
The programs are 32 bit ones. Wine is not involved.

I was able to get the official libllvm3.1 installed. Then I was able to install libgl1-mesa-dri:i386. This appears to have fixed the issue. I can get one of the programs to open up now no problem.

However another one does not do anything. It no longer gives me errors but it does not open either.

Since the driver issue is resolved I will mark this as solved.

Thank you for the help. :D

---

### Post by aldeby on 2013-02-10
google earth is a 32 bit only program. On 64 bit architecture it requires 32 bit drivers:

```
sudo apt-get install libgl1-mesa-dri:i386
```

---

