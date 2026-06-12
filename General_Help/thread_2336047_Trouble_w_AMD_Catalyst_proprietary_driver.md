---
title: "Trouble w AMD Catalyst proprietary driver"
date: 2016-09-03
forum: General Help
---

### Post by bedina on 2016-09-03
john@john-Vostro-1700:~$ sudo sh ~/Downloads/fglr*/*.run
Created directory fglrx-install.zhBe9a
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-14.301.1001...........................................................................=======================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

error: Detected X Server version 'XServer 1.18.3' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:i686:lib:XServer 1.18.3:none:4.4.0-36-generic:)
Installation will not proceed.

Removing temporary directory: fglrx-install.zhBe9a
john@john-Vostro-1700:~$ 
                                                                                                                                                                                                          
                                                                                                                                 
                                   
I tried to correct this by apt-get install X.Org 6.9 and Xserver 1.10.  Both of which download and install but when I go to run the program with the top command I get the same error as before I downloaded and installed.What am I missing here?

---

### Post by QIII on 2016-09-04
Hello!

What release of Ubuntu are you running?

---

### Post by bedina on 2016-09-04
This is in kubuntu 16.04

---

### Post by autocrat on 2016-09-04
Maybe I am reading this wrong, but 16.04 does not look supported.

[http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx)

---

### Post by QIII on 2016-09-07
fglrx will not work the the X Server version used by Xenial.  AMD has not updated it to do so.  There have been rumors that they might, but I think now that it really was only rumor.

With 16.04, the installer determines the GPU model and, as appropriate, installs either the open source Radeon driver or the open source AMDGPU driver.  AMDGPU only works with technologically compatible GPUs, so it is not available for all models.

If AMDGPU is installed, it is likely that the open source-based AMDGPU-PRO proprietary driver can be installed.  I am using that for both Yakkety and Xenial with a supported card.

Consider fglrx gone from Xenial forward.

---

