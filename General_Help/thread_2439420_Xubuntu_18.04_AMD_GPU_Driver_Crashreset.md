---
title: "Xubuntu 18.04 AMD GPU Driver Crash/reset"
date: 2020-03-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-03-27
Any idea what caused this? it happened while the system was idle and i was not present at the time, recovered using ssh and restarting lightdm
from dmesg:
[FONT=courier new][drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to initialize parser -125!
Full log file for everything that happened today: [ATTACH]285327[/ATTACH][/FONT]
```

~$ uname -r
5.3.0-42-generic

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

~$ apt-cache policy mesa-*
mesa-opencl-icd:
  Installed: (none)
  Candidate: 19.2.8-0ubuntu0~18.04.3
  Version table:
     19.2.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
mesa-glide2-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
mesa-common-dev:
  Installed: 19.2.8-0ubuntu0~18.04.3
  Candidate: 19.2.8-0ubuntu0~18.04.3
  Version table:
 *** 19.2.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
mesa-utils:
  Installed: 8.4.0-1
  Candidate: 8.4.0-1
  Version table:
 *** 8.4.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
mesa-utils-extra:
  Installed: (none)
  Candidate: 8.4.0-1
  Version table:
     8.4.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
mesa-test-tools:
  Installed: (none)
  Candidate: (none)
  Version table:
mesa-vdpau-drivers:
  Installed: 19.2.8-0ubuntu0~18.04.3
  Candidate: 19.2.8-0ubuntu0~18.04.3
  Version table:
 *** 19.2.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
mesa-vulkan-drivers:
  Installed: 19.2.8-0ubuntu0~18.04.3
  Candidate: 19.2.8-0ubuntu0~18.04.3
  Version table:
 *** 19.2.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
mesa-va-drivers:
  Installed: 19.2.8-0ubuntu0~18.04.3
  Candidate: 19.2.8-0ubuntu0~18.04.3
  Version table:
 *** 19.2.8-0ubuntu0~18.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

~$ apt-cache policy libdrm-radeon1 xserver-xorg-video-radeon
libdrm-radeon1:
  Installed: 2.4.99-1ubuntu1~18.04.2
  Candidate: 2.4.99-1ubuntu1~18.04.2
  Version table:
 *** 2.4.99-1ubuntu1~18.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.4.91-2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
xserver-xorg-video-radeon:
  Installed: 1:18.0.1-1
  Candidate: 1:18.0.1-1
  Version table:
 *** 1:18.0.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Yellow Pasque on 2020-03-27
```
kernel: [128598.641215] [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process tumblerd pid 8388 thread tumblerd:cs0 pid 8430
```

Tumbler thumbnailer misbehaving?

---

