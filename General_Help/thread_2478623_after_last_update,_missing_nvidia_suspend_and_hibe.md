---
title: "after last update, missing nvidia suspend and hibernate services"
date: 2022-08-31
forum: General Help
---

### Post by protektwar on 2022-08-31
Hello,

I have notice that after my last Ubuntu update, my desktop it will not be able to perform any suspend or hibernate modes, instead I'm getting a log out.
Is there anybody else having that issue?

I have the symbolic link:
/etc/systemd/system/systemd-hibernate.service.requires
0 lrwxrwxrwx  1 root root   44 Apr 23 14:36 nvidia-hibernate.service -> /lib/systemd/system/nvidia-hibernate.service
0 lrwxrwxrwx  1 root root   41 Apr 23 14:36 nvidia-resume.service -> /lib/systemd/system/nvidia-resume.service
/etc/systemd/system/systemd-suspend.service.requires
0 lrwxrwxrwx  1 root root   41 Apr 23 14:36 nvidia-resume.service -> /lib/systemd/system/nvidia-resume.service
0 lrwxrwxrwx  1 root root   42 Apr 23 14:36 nvidia-suspend.service -> /lib/systemd/system/nvidia-suspend.service

but the files are missing from /lib/systemd/system and /usr/share/doc/nvidia-driver-515/. I have searched for them on my system and are no where to be found... 
nvidia-hibernate.service
nvidia-resume.service 
 nvidia-suspend.service

Kernel: 5.15.0-46-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
Distro: Ubuntu 20.04.5 LTS (Focal Fossa) 
Graphics:  Device-1: NVIDIA GA106 [GeForce RTX 3060 Lite Hash Rate] vendor: ASUSTeK driver: nvidia v: 515.65.01 
           bus ID: 08:00.0 chip ID: 10de:2504 
           Display: x11 server: X.Org 1.20.13 driver: nvidia compositor: gnome-shell 
           resolution: 1920x1080~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: NVIDIA GeForce RTX 3060/PCIe/SSE2 v: 4.6.0 NVIDIA 515.65.01 direct render: Yes 

Regards,
Alexandru

---

