---
title: "Newest Jammy kernel (5.15.0-30) loads nouveau instead of nvidia driver"
date: 2022-05-13
forum: General Help
---

### Post by Wise Ferret on 2022-05-13
I use nvidia rtx 3070ti.
After latest kernel upgrade (5.15.0-30), ubuntu loads the nouveau driver instead of the proprietary nvidia driver. When I run the former kernel (5.15.0-27), the nvidia driver loads properly.

Here is [dmesg output]("https://paste.ubuntu.com/p/6W9c32hJkv/").

Is there any idea of the possible problem? What should I look for?

---

### Post by TheFu on 2022-05-13
dkms is the subsystem that re-links objects for a new kernel.  Sometimes that becomes confused.  On my system with an older, weaker, nVidia GPU, I'd reinstall the nvidia driver packages and the generic dkms package to get it working.
```
$ dpkg -l nvidia-dk*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version         Architecture    Description
+++-=====================-===============-===============-================================================
rc  nvidia-dkms-460       460.39-0ubuntu0 amd64           NVIDIA DKMS package
rc  nvidia-dkms-460-serve 460.73.01-0ubun amd64           NVIDIA DKMS package
[COLOR="#008000"]ii  nvidia-dkms-470       470.103.01-0ubu amd64           NVIDIA DKMS package[/COLOR]
un  nvidia-dkms-kernel    <none>          <none>          (no description available)
```
I'm on an older release, but suspect this will do no harm and might fix it.  Of course, your versions will be different than mine.

---

### Post by Wise Ferret on 2022-05-13
Problem solved! linux-headers-generic was not installed. Once installed, I re-installed nvidia-dkms-510 and rebooted, and the driver loads fine.
Thanks for directing me toward the problem.

---

