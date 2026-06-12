---
title: "Ubuntu 14.04.3 64 bit LTS hardware enablement stack errors"
date: 2015-08-06
forum: General Help
---

### Post by Welly Wu on 2015-08-06
[FONT=arial]```
wellywu@ZaReasonZeto:~$ uname -r
3.16.0-45-generic
wellywu@ZaReasonZeto:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty
wellywu@ZaReasonZeto:~$ sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libwayland-egl1-mesa-lts-vivid : Depends: libegl1-mesa-lts-vivid (= 10.5.2-0ubuntu1~trusty1) but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 xserver-xorg-core-lts-vivid : Depends: libgbm1-lts-vivid (>= 8.1~0) but it is not going to be installed
                               Recommends: libgl1-mesa-dri-lts-vivid (>= 7.10.2-4) but it is not going to be installed
 xserver-xorg-lts-vivid : Recommends: libgl1-mesa-dri-lts-vivid but it is not going to be installed
                          Recommends: libgl1-mesa-glx-lts-vivid but it is not going to be installed
                          Recommends: libegl1-mesa-lts-vivid but it is not going to be installed
                          Recommends: libegl1-mesa-drivers-lts-vivid but it is not installable
                          Recommends: libgbm1-lts-vivid but it is not going to be installed
                          Recommends: libgles2-mesa-lts-vivid but it is not going to be installed
                          Recommends: libgles1-mesa-lts-vivid but it is not going to be installed
                          Conflicts: libegl1-mesa (>= 0~)
                          Conflicts: libgl1-mesa-dri (>= 0~)
                          Conflicts: libgl1-mesa-dri:i386 (>= 0~)
                          Conflicts: libgl1-mesa-glx (>= 0~)
                          Conflicts: libgl1-mesa-glx:i386 (>= 0~)
                          Conflicts: libglapi-mesa (>= 0~)
                          Conflicts: libglapi-mesa:i386 (>= 0~)
                          Conflicts: libgles1-mesa (>= 0~)
                          Conflicts: libgles2-mesa (>= 0~)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
wellywu@ZaReasonZeto:~$
```
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I get this error when I try to install the latest Ubuntu 14.04.3 64 bit LTS hardware enablement stack. Do I have to remove the X.Org-Edgers PPA, restart my ZaReazon Zeto desktop PC, and try to install the new hardware enablement stack again and then re-add and reinstall the latest X.Org-Edgers PPA again?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Please let me know what I have to do to fix this problem. Thank you.[/FONT]

---

### Post by monkeybrain20122 on 2015-08-06
Yes you have to purge xorg-edgers ppa, it is not compatible with hardware enablement stack as it is stated on its webpage. If xorg-edgers is working well why do you need the hardware enablement stack? xorg-edgers has newer graphic driver than HES anyway and in general it is a bad idea to upgrade your graphic stack (or any package for that matter) with more than one sources even if that doesn't create problems right the way. If you need a new kernel for whatever reason just grab it from mainline.

---

### Post by Welly Wu on 2015-08-06
I reinstalled Ubuntu 14.04.3 64 bit LTS GNU/Linux on my ZaReason Zeto desktop PC bare metal from scratch earlier this afternoon. This solved my problem with the LTS hardware enablement stack. I'm going to reinstall Ubuntu 14.04.3 64 bit LTS GNU/Linux on my Lenovo IdeaPad Y510P notebook PC tomorrow afternoon again. I learned that both the mc3man and X.Org Edgers PPAs are not compatible with newer LTS hardware enablement stacks so I didn't re-add them on my ZaReason Zeto desktop PC nor will I re-add them on my Lenovo IdeaPad Y510P notebook PC tomorrow again either. I should be clear for Ubuntu 14.04.4 64 bit LTS GNU/Linux in February 2016 and then Ubuntu 16.04 64 bit LTS GNU/Linux in April 2016 barring any unforeseeable future problems. I'm also trying harder to install less software applications, packages, libraries, and dependencies and I'm keeping my Ubuntu Unity desktop environment as minimal and clean as possible. This should accelerate logging into my Ubuntu Administrator account and Ubuntu Unity desktop environment considerably. I had way too much junk in previous installations.

---

### Post by mc4man on 2015-08-06
```
 I learned that both the mc3man and X.Org Edgers PPAs are not compatible with newer LTS hardware enablement stacks so...
```
edgers yes, the multimedia ppa is quite fine with 14.04.3, I'm using it right now with no issues. Likely something from your side...
(and I'm using a Lenovo-IdeaPad-Y510P

---

### Post by Welly Wu on 2015-08-06
Perhaps I was wrong about the mc3man PPA. I think that I'll avoid it in future installations because I don't really have a need for it. Ubuntu-restricted-extras and J River Media Center seem to take care of audio and video codecs that I own just fine.

---

### Post by Welly Wu on 2015-08-07
I reinstalled Ubuntu 14.04.3 64 bit LTS GNU/Linux and my favorite software applications, packages, libraries, and dependencies on my Lenovo IdeaPad Y510P notebook PC. It took roughly three hours to complete and it is nearly identical to my ZaReason Zeto desktop PC in terms of the installed software in Ubuntu. Now, I learned to avoid the X.Org Edgers PPA so that I can upgrade to Ubuntu 14.04.4 64 bit LTS GNU/Linux and Ubuntu 16.04 64 bit LTS GNU/Linux in the future and beyond. I don't want to have to reinstall from scratch again for a long period of time. I shall see exactly how long of a period of time that will take.

---

