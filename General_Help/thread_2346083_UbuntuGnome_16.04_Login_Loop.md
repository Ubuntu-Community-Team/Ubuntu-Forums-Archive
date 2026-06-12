---
title: "UbuntuGnome 16.04 Login Loop"
date: 2016-12-11
forum: General Help
---

### Post by JustJazz on 2016-12-11
After getting my partition issues sorted out I reinstalled Ubuntu, this time going with UbuntuGnome 16.04 which I triple boot with Window 7 and Xubuntu 16.04. Windows 7 and Xubuntu 16.04 run great but after installing UbuntuGnome 16.04 [COLOR=#000000]I didn't get the chance to install Nvidia Server Settings before having to reboot to a black screen. I purged all old drivers, installed correct Nvidia drivers 3.04.132 in terminal and now I get this Login Loop at the login screen. I never had this problem in 2+ yrs. when I triple booted Windows 7, Linux Mint and Ubuntu 14.04 LTS  w/Gnome shell. I've tried the "Nomodeset" and ".Xauthority" tricks but no dice[/COLOR]](*,) #-o

lspci | grep VGA:
```
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
```

[COLOR=#000000]dpkg -l | grep -i nvidia:

[/COLOR]```

ii  libcuda1-304                                  304.132-0ubuntu0.16.04.2                      amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                    304.132-0ubuntu0.16.04.2                      amd64        NVIDIA legacy binary driver - version 304.132
ii  nvidia-opencl-icd-304                         304.132-0ubuntu0.16.04.2                      amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                               361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver

```

[COLOR=#000000]dkms status:

[/COLOR]```
nvidia-304, 304.132, 4.4.0-47-generic, x86_64: installed
nvidia-304, 304.132, 4.4.0-51-generic, x86_64: installed
nvidia-304, 304.132, 4.4.0-53-generic, x86_64: installed

```

---

