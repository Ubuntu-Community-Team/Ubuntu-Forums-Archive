---
title: "LTSP apt problems"
date: 2008-03-27
forum: General Help
---

### Post by keenboy on 2008-03-27
I have an Ubuntu 7.10 LTSP Server. When I use apt to install software into the chrooted ltsp environment (/opt/ltsp/i386/) I get the following errors:

```
Need to get 0B/18.7MB of archives.
After unpacking 225kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 16352 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-386 2.6.22-14.46 (using .../linux-image-2.6.22-14-386_2.6.22-14.46_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-386 ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.22-14-386.postrm line 320.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 320.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-386_2.6.22-14.46_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 320.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-386_2.6.22-14.46_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm not convinced that apt is actually installing the software I would like it to.

Does anybody know hy this could be?

Thanks

---

