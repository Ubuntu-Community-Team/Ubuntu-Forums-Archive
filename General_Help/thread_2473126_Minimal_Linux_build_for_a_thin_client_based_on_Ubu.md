---
title: "Minimal Linux build for a thin client based on Ubuntu/Debian"
date: 2022-03-24
forum: General Help
---

### Post by akexanderzhirov on 2022-03-24
There are thin clients running a distribution built in Buildroot.
There are practically no packages in the client itself. Device drivers  are loaded over the network - mainly drivers for the video card. The  distribution itself without video card drivers weighs about 10  megabytes. The distribution itself has an RDP client installed (most  likely a self-written one). I'm sharing an executable package that I pulled from there via ssh
The bottom line is that clients are loaded and there is only one RDP  client icon on the desktop and no additional features. Everything is cut  out. The distribution is loaded over the network as PXE.
  The gap is that new workstations have appeared and this distribution  does not rise on them due to the lack of drivers for the video card.
  I do not have the source code of Buildroot, in which this  distribution was built. Therefore, it became necessary to build a  similar new distribution with support for a fresh (not necessarily the  latest) kernel.

**   Requirements:**

[LIST]
[*]ssh 
[*]openbox/fluxbox 
[*]rdp
[*]midnight commander 
[*]minimum **rootfs** size, preferably up to 20 MB 
[/LIST]
    It just turns out that I'm picking up the x86_64 distribution for a  written RDP application. It is desirable for me to use it in the  distribution.
Is there any manual or an example of an assembly with unnecessary packages cut out as much as possible, so that the PC just loads, the desktop appears and a single RDP icon?
  Are there any suggestions?

---

### Post by him610 on 2022-03-26
You could probably download and install the server or 'core' version of *buntu/Debian followed by installing your required programs.

---

### Post by CharlesA on 2022-03-26
It sounds like you are looking for a kiosk mode. See here:
[https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview](https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview)

Theoretically, you should be able to do a PXE boot of a predefined image, but that's much more complicated than just installing it on bare metal.

As a staff member: I have removed the links in the OP - You mentioned Buildroot and the official page can be found here: [https://buildroot.org/](https://buildroot.org/)

---

### Post by Tadaen_Sylvermane on 2022-03-26
Ltsp.org

Can customize it. 100% network based.

---

### Post by akexanderzhirov on 2022-05-12
> **CharlesA said:**
> It sounds like you are looking for a kiosk mode. See here:
[https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview](https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview)

It is interesting. Thanks. It will be necessary to study.

---

