---
title: "dpkg returned an error code (1)"
date: 2018-10-31
forum: General Help
---

### Post by fanezeu on 2018-10-31
[COLOR=#000000]Hello there. [/COLOR]

[COLOR=#000000]I'm having a situation that i can not resolve . I can't install anything because of the following errors. This happens with everything i try to install or when i try apt-get upgrade , autoremove , etc[/COLOR]



```
root@ubuntu:~# sudo apt install qemu-kvm libvirt-binReading package lists... Done
Building dependency tree
Reading state information... Done
libvirt-bin is already the newest version (4.0.0-1ubuntu8.5).
qemu-kvm is already the newest version (1:2.12+dfsg-3).
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Setting up libvirt-daemon-system (4.7.0-1) ...
virtlockd.service is a disabled or a static unit, not starting it.
Job for libvirtd.service failed because the control process exited with error code.
See "systemctl status libvirtd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript libvirtd, action "restart" failed.
&#9679; libvirtd.service - Virtualization daemon
   Loaded: loaded (/lib/systemd/system/libvirtd.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Wed 2018-10-31 14:34:15 EET; 3ms ago
     Docs: man:libvirtd(8)
           https://libvirt.org
  Process: 19044 ExecStart=/usr/sbin/libvirtd $libvirtd_opts (code=exited, status=6)
 Main PID: 19044 (code=exited, status=6)
dpkg: error processing package libvirt-daemon-system (--configure):
 installed libvirt-daemon-system package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libvirt-bin:
 libvirt-bin depends on libvirt-daemon-system (>= 4.0.0-1ubuntu8.5); however:
  Package libvirt-daemon-system is not configured yet.


dpkg: error processing package libvirt-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                Errors were encountered while processing:
 libvirt-daemon-system
 libvirt-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


[COLOR=#000000]Can someone please help me? I've tried everything that i could find on ubuntu forums or other forums. [/COLOR]


[COLOR=#000000]Thank you.[/COLOR]

---

### Post by Impavidus on 2018-10-31
I don't know about libvirt-bin or libvirt-daemon-system, but I see that the package manager tries to install libvirt-bin version 4.0.0-1ubuntu8.5 (which is the latest version in the repositories for Ubuntu 18.04), but libvirt-daemon-system version 4.7.0-1, which is not in the official repositories. Both packages are absent from the repositories for Ubuntu 18.10. So which version of Ubuntu are you running? And were did you get libvirt-daemon-system 4.7? Because this strange version could be the cause of your problem.

Show us this:```
apt-cache policy libvirt-bin libvirt-daemon-system
```

---

### Post by fanezeu on 2018-10-31
Hi , thnaks for the reply

```
root@ubuntu:~# apt-cache policy libvirt-bin libvirt-daemon-systemlibvirt-bin:
  Installed: 4.0.0-1ubuntu8.5
  Candidate: 4.0.0-1ubuntu8.5
  Version table:
 *** 4.0.0-1ubuntu8.5 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packag                                                                                                                                                             es
        100 /var/lib/dpkg/status
     4.0.0-1ubuntu8.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Package                                                                                                                                                             s
     4.0.0-1ubuntu8 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
     2.5.0-3ubuntu5.6 500
        500 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty-updates/main amd64 Packa                                                                                                                                                             ges
     2.5.0-3ubuntu5 500
        500 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty/main amd64 Packages
libvirt-daemon-system:
  Installed: 4.7.0-1
  Candidate: 4.7.0-1
  Version table:
 *** 4.7.0-1 100
        100 /var/lib/dpkg/status
     4.0.0-1ubuntu8.5 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packag                                                                                                                                                             es
     4.0.0-1ubuntu8.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Package                                                                                                                                                             s
     4.0.0-1ubuntu8 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
     2.5.0-3ubuntu5.6 500
        500 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty-updates/main amd64 Packa                                                                                                                                                             ges
     2.5.0-3ubuntu5 500
        500 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty/main amd64 Packages
```

---

### Post by Impavidus on 2018-10-31
There isn't even a source for 4.7.0-1.

I suppose you can try and downgrade libvirt-daemon-system to the right version:```
sudo apt-get install libvirt-daemon-system=4.0.0-1ubuntu8.5
```

I see you also have some zesty repositories from the old releases server activated. You can disable those.

BTW, if you're already in a root shell, there's no need for sudo.

---

