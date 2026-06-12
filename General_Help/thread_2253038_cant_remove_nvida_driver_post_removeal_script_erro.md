---
title: "cant remove nvida driver post removeal script error"
date: 2014-11-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-11-16
I am using the xorg edgers ppa, iwas going to update to the 346.18 driver, so i go to remove my 340.58 driver and i can't
```
~$ sudo apt-get purge nvidia-340 screen-resolution-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-340* screen-resolution-extra*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 268 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 312619 files and directories currently installed.)
Removing nvidia-340 (340.58-0ubuntu1~xedgers14.04.1) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-340-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-340-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
stop: Unknown instance: 
userdel: user nvidia-persistenced is currently used by process 1429
dpkg: error processing package nvidia-340 (--purge):
 subprocess installed post-removal script returned error exit status 8
Removing screen-resolution-extra (0.17.1) ...
Purging configuration files for screen-resolution-extra (0.17.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 nvidia-340
E: Sub-process /usr/bin/dpkg returned an error code (1)]
```
[[img]http://www.zimagez.com/miniature/screenshot-11162014-054627pm.php[/img]](http://www.zimagez.com/zimage/screenshot-11162014-054627pm.php)

---

### Post by Aide9aic on 2014-11-17
The post-removal script in the package is trying to stop the **nvidia-persistenced** process, but there seems to be a bug -- it isn't finding the process. However, the output does tell you the PID. Notice the line **userdel: user nvidia-persistenced is currently used by process 1429**. So just kill that process:
```
sudo kill -9 1429
```
Now run the removal process again. This will finish the uninstallation. Then you can proceed with the update.

However, you may find another problem: on my laptop, at least, the driver is convinced that I have an external monitor attached to the VGA port, when in fact I do not. [See my post to Kubuntu Forums]("https://www.kubuntuforums.net/showthread.php?66869") describing the problem. I came to Ubuntu Forum to search for anyone with the similar issue. Meanwhile, I saw your post, and had encountered the same problem, so I wanted to share how I worked around it.

---

### Post by pqwoerituytrueiwoq on 2014-11-17
thanks, now have it installed :) now lets see what we can do here
worst case scenario i ssh in and revert it using my laptop which i hope will run given the power cord is failing
NO VGA issues here :)
[[IMG]http://www.zimagez.com/miniature/screenshot-11172014-110521pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-11172014-110521pm.php")
but i removed bbswitch-dkms and nvidia-prive
```
~$ cat /var/log/Xorg.0.log|grep -i crt
[     8.789] (--) NVIDIA(0):     CRT-0
[     8.789] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
```

---

