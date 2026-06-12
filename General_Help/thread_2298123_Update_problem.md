---
title: "Update problem"
date: 2015-10-08
forum: General Help
---

### Post by johncrossley81 on 2015-10-08
I think I've got the same issue.  But I don't think it's the kernel.

I've tried to boot all these kernels:
 3.19.0-31
3.19.0-30
3.13.0-66
3.13.0-65
3.2.0-91

And they all result in a crash within a few minutes of running.

I think it's one of the other updates pushed out today, but I don't know at this point which one:

[from /var/log/apt/history.log]

Start-Date: 2015-10-08  10:16:29
Commandline: aptdaemon role='role-commit-packages' sender=':1.93'
Install: linux-image-extra-3.19.0-31-generic:amd64 (3.19.0-31.35~14.04.1), linux-image-3.19.0-31-generic:amd64 (3.19.0-31.35~14.04.1), linux-headers-3.19.0-31-generic:amd64 (3.19.0-31.35~14.04.1), linux-image-extra-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-image-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-headers-3.13.0-66:amd64 (3.13.0-66.107), linux-headers-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-headers-3.19.0-31:amd64 (3.19.0-31.35~14.04.1)
Upgrade:  lxc:amd64 (1.0.7-0ubuntu0.6, 1.0.7-0ubuntu0.7), libsystemd-login0:amd64  (204-5ubuntu20.14, 204-5ubuntu20.15), linux-headers-generic:amd64  (3.13.0.65.71, 3.13.0.66.72), systemd-services:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libsystemd-daemon0:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libgudev-1.0-0:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libpam-systemd:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), linux-image-generic-lts-vivid:amd64  (3.19.0.30.17, 3.19.0.31.18), udev:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), gir1.2-gudev-1.0:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1.1,  0.12.4-0nocelt2ubuntu1.2), libudev1:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libudev1:i386 (204-5ubuntu20.14, 204-5ubuntu20.15),  linux-headers-generic-lts-vivid:amd64 (3.19.0.30.17, 3.19.0.31.18),  python3-lxc:amd64 (1.0.7-0ubuntu0.6, 1.0.7-0ubuntu0.7), liblxc1:amd64  (1.0.7-0ubuntu0.6, 1.0.7-0ubuntu0.7), libsystemd-journal0:amd64  (204-5ubuntu20.14, 204-5ubuntu20.15), linux-generic-lts-vivid:amd64  (3.19.0.30.17, 3.19.0.31.18), lxc-templates:amd64 (1.0.7-0ubuntu0.6,  1.0.7-0ubuntu0.7), linux-libc-dev:amd64 (3.13.0-65.106, 3.13.0-66.107),  linux-image-generic:amd64 (3.13.0.65.71, 3.13.0.66.72)
End-Date: 2015-10-08  10:20:11

Start-Date: 2015-10-08  10:30:25
Commandline: aptdaemon role='role-commit-packages' sender=':1.88'
Upgrade:  librbd1:amd64 (0.80.10-0ubuntu1.14.04.2, 0.80.10-0ubuntu1.14.04.3),  librados2:amd64 (0.80.10-0ubuntu1.14.04.2, 0.80.10-0ubuntu1.14.04.3)
End-Date: 2015-10-08  10:30:27

Any ideas?

Cheers,

John

---

### Post by frogotronic on 2015-10-08
> **johncrossley81 said:**
> I think I've got the same issue.  But I don't think it's the kernel.

I've tried to boot all these kernels:
 3.19.0-31
3.19.0-30
3.13.0-66
3.13.0-65
3.2.0-91

And they all result in a crash within a few minutes of running.

I think it's one of the other updates pushed out today, but I don't know at this point which one:

[from /var/log/apt/history.log]

Start-Date: 2015-10-08  10:16:29
Commandline: aptdaemon role='role-commit-packages' sender=':1.93'
Install: linux-image-extra-3.19.0-31-generic:amd64 (3.19.0-31.35~14.04.1), linux-image-3.19.0-31-generic:amd64 (3.19.0-31.35~14.04.1), linux-headers-3.19.0-31-generic:amd64 (3.19.0-31.35~14.04.1), linux-image-extra-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-image-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-headers-3.13.0-66:amd64 (3.13.0-66.107), linux-headers-3.13.0-66-generic:amd64 (3.13.0-66.107), linux-headers-3.19.0-31:amd64 (3.19.0-31.35~14.04.1)
Upgrade:  lxc:amd64 (1.0.7-0ubuntu0.6, 1.0.7-0ubuntu0.7), libsystemd-login0:amd64  (204-5ubuntu20.14, 204-5ubuntu20.15), linux-headers-generic:amd64  (3.13.0.65.71, 3.13.0.66.72), systemd-services:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libsystemd-daemon0:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libgudev-1.0-0:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libpam-systemd:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), linux-image-generic-lts-vivid:amd64  (3.19.0.30.17, 3.19.0.31.18), udev:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), gir1.2-gudev-1.0:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libspice-server1:amd64 (0.12.4-0nocelt2ubuntu1.1,  0.12.4-0nocelt2ubuntu1.2), libudev1:amd64 (204-5ubuntu20.14,  204-5ubuntu20.15), libudev1:i386 (204-5ubuntu20.14, 204-5ubuntu20.15),  linux-headers-generic-lts-vivid:amd64 (3.19.0.30.17, 3.19.0.31.18),  python3-lxc:amd64 (1.0.7-0ubuntu0.6, 1.0.7-0ubuntu0.7), liblxc1:amd64  (1.0.7-0ubuntu0.6, 1.0.7-0ubuntu0.7), libsystemd-journal0:amd64  (204-5ubuntu20.14, 204-5ubuntu20.15), linux-generic-lts-vivid:amd64  (3.19.0.30.17, 3.19.0.31.18), lxc-templates:amd64 (1.0.7-0ubuntu0.6,  1.0.7-0ubuntu0.7), linux-libc-dev:amd64 (3.13.0-65.106, 3.13.0-66.107),  linux-image-generic:amd64 (3.13.0.65.71, 3.13.0.66.72)
End-Date: 2015-10-08  10:20:11

Start-Date: 2015-10-08  10:30:25
Commandline: aptdaemon role='role-commit-packages' sender=':1.88'
Upgrade:  librbd1:amd64 (0.80.10-0ubuntu1.14.04.2, 0.80.10-0ubuntu1.14.04.3),  librados2:amd64 (0.80.10-0ubuntu1.14.04.2, 0.80.10-0ubuntu1.14.04.3)
End-Date: 2015-10-08  10:30:27

Any ideas?

Cheers,

John

Yep, "me too".  Kernel 3.13.0-66-generic running on a 12.04.5 LTS background crashes on login, or else hangs the GUI.  Reboot & HOLD the RT Shift key down, and select older kernel.  This *-66 one's a bust!

Regards,
Andor

---

### Post by howefield on 2015-10-09
Hello johncrossley81 and welcome to the forum, I have moved your post to a new thread of its own as it doesn't sound the same as the thread you posted in.

Does a specific action trigger crash, is it reproducible or random ?

---

