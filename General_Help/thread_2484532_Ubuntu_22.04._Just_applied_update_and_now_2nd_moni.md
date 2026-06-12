---
title: "Ubuntu 22.04. Just applied update and now 2nd monitor not working!"
date: 2023-03-02
forum: General Help
---

### Post by peterx14 on 2023-03-02
Hi all,

After booting today (2023-03-02) I had a warning icon in the task-bar (red-circle with horizontal white line in centre), and I'm sorry I didn't note exactly what it was saying, but something about the update not working... or starting... or something. Anyway, I applied updates which appeared to include kernel headers. After that there were further updates which was unexpected, but those I'm fairly certain did involve a kernel update and it then requested a reboot.

Since reboot, my second monitor no longer works. I've rebooted with an Ubuntu Boot USB stick and confirmed that the monitor is indeed still working.

The other thing is, all desktop animations have stopped. Specific things I've noticed:
[LIST]
[*]When the screen saver starts, it no longer gradually fades out. The screen just goes blank.
[*]When switching between work-spaces, it just immediately jumps to the next/prev workspace without any animation indicating which direction it is in.
[/LIST]

After my reboot, from a terminal I ran "sudo apt update" and could see 80 updates! I then did "sudo apt upgrade" and that has applied 5 of those updates, but apparently there's a lot of updates being held back. I'll list those along with my current setup:

```
$ uname -a
Linux kafka 5.19.0-35-generic #36~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb 17 15:17:25 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

$ echo $XDG_SESSION_TYPE
x11
```

I have an nVidia GT1030 (2GB) video card, and according to "Additional Drivers", I am running "nvidia-driver-525 (proprietary, tested)". Although it *may* be of note that when I just Googled how to get my nVidia version from the command line, the following command appears to have failed:

```
$ sudo nvidia-smi 
[sudo] password for pryan: 
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```

And here's the list of all the packages being held back:
```
$ apt list --upgradable 
Listing... Done
fonts-opensymbol/jammy-updates,jammy-updates 2:102.12+LibO7.3.7-0ubuntu0.22.04.2 all [upgradable from: 2:102.12+LibO7.3.7-0ubuntu0.22.04.1]
gir1.2-pango-1.0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
gnome-remote-desktop/jammy-updates 42.7-0ubuntu1 amd64 [upgradable from: 42.4-0ubuntu1]
grub-efi-amd64-bin/jammy-updates 2.06-2ubuntu14.1 amd64 [upgradable from: 2.06-2ubuntu10]
grub-efi-amd64-signed/jammy-updates 1.187.3~22.04.1+2.06-2ubuntu14.1 amd64 [upgradable from: 1.182~22.04.1+2.06-2ubuntu10]
libmbim-glib4/jammy-updates 1.28.0-1~ubuntu20.04.1 amd64 [upgradable from: 1.26.2-1build1]
libmbim-proxy/jammy-updates 1.28.0-1~ubuntu20.04.1 amd64 [upgradable from: 1.26.2-1build1]
libmm-glib0/jammy-updates 1.20.0-1~ubuntu22.04.1 amd64 [upgradable from: 1.18.6-1]
libnvidia-cfg1-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-common-525/jammy-updates,jammy-updates 525.85.05-0ubuntu0.22.04.1 all [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-compute-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-compute-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 i386 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-decode-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-decode-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 i386 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-encode-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-encode-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 i386 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-extra-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-fbc1-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-fbc1-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 i386 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-gl-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libnvidia-gl-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 i386 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
libpango-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libpango-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 i386 [upgradable from: 1.50.6+ds-2]
libpangocairo-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libpangocairo-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 i386 [upgradable from: 1.50.6+ds-2]
libpangoft2-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libpangoft2-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 i386 [upgradable from: 1.50.6+ds-2]
libpangoxft-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libqmi-glib5/jammy-updates 1.32.0-1ubuntu0.22.04.1 amd64 [upgradable from: 1.30.4-1]
libqmi-proxy/jammy-updates 1.32.0-1ubuntu0.22.04.1 amd64 [upgradable from: 1.30.4-1]
libreoffice-base-core/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-calc/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-common/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-core/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-draw/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-gnome/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-gtk3/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-help-common/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-help-en-gb/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-help-en-us/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-impress/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-l10n-en-gb/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-math/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-ogltrans/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-pdfimport/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-style-breeze/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-style-colibre/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-style-elementary/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-style-yaru/jammy-updates,jammy-updates 1:7.3.7-0ubuntu0.22.04.2 all [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libreoffice-writer/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libsnmp-base/jammy-updates,jammy-updates 5.9.1+dfsg-1ubuntu2.5 all [upgradable from: 5.9.1+dfsg-1ubuntu2.4]
libsnmp40/jammy-updates 5.9.1+dfsg-1ubuntu2.5 amd64 [upgradable from: 5.9.1+dfsg-1ubuntu2.4]
libuno-cppu3/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libuno-cppuhelpergcc3-3/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libuno-purpenvhelpergcc3-3/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libuno-sal3/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
libuno-salhelpergcc3-3/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
linux-modules-nvidia-525-generic-hwe-22.04/jammy-updates,jammy-security 5.19.0-35.36~22.04.1 amd64 [upgradable from: 5.19.0-32.33~22.04.1]
modemmanager/jammy-updates 1.20.0-1~ubuntu22.04.1 amd64 [upgradable from: 1.18.6-1]
ncat/jammy-updates 7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 amd64 [upgradable from: 7.91+dfsg1+really7.80+dfsg1-2build1]
nmap-common/jammy-updates,jammy-updates 7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 all [upgradable from: 7.91+dfsg1+really7.80+dfsg1-2build1]
nmap/jammy-updates 7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 amd64 [upgradable from: 7.91+dfsg1+really7.80+dfsg1-2build1]
nvidia-compute-utils-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
nvidia-driver-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
nvidia-kernel-common-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
nvidia-kernel-source-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
nvidia-utils-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]
python3-software-properties/jammy-updates,jammy-updates 0.99.22.6 all [upgradable from: 0.99.22.4]
python3-uno/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
shim-signed/jammy-updates 1.51.3+15.7-0ubuntu1 amd64 [upgradable from: 1.51+15.4-0ubuntu9]
software-properties-common/jammy-updates,jammy-updates 0.99.22.6 all [upgradable from: 0.99.22.4]
software-properties-gtk/jammy-updates,jammy-updates 0.99.22.6 all [upgradable from: 0.99.22.4]
uno-libs-private/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
ure/jammy-updates 1:7.3.7-0ubuntu0.22.04.2 amd64 [upgradable from: 1:7.3.7-0ubuntu0.22.04.1]
xserver-xorg-video-nvidia-525/jammy-updates 525.85.05-0ubuntu0.22.04.1 amd64 [upgradable from: 525.78.01-0ubuntu0.22.04.1]

```

There's a ton of stuff in logs, e.g. syslog, but... even when things are working, there's a ton of stuff that gets logged, so I've no idea what's useful to post.

Anyway, any help gratefully received!! :D

---

### Post by peterx14 on 2023-03-02
Minor update: I noticed that the screen-saver just blanks the screen, but the monitor back-light remains on.

---

### Post by peterx14 on 2023-03-02
It's a lot quieter here than it used to be!!

I tried to boot using an older kernel, but I'm booting using EFI so apparently I use ESC rather than SHIFT to get the grub menu... but I've not been successful with that just yet. I did get in one but I hit ESC again and got the GRUB> prompt... at which point it was insanely slow to respond and in any case, I don't know how to use that to get back to it's menu or indeed to just boot from an older kernel. So I ended up rebooting.

More excitingly, I discovered this in syslog:
```
Mar  2 15:13:28 kafka gdm3[3986]: modprobe: FATAL: Module nvidia not found in directory /lib/modules/5.19.0-35-generic

```

Which suggests that perhaps my nVidia drivers are not loading and I guess that'd explain everything. I don't know if any of the following help, but here's what I tried/got:
```
$ dkms status
virtualbox/6.1.38, 5.19.0-32-generic, x86_64: installed
virtualbox/6.1.38, 5.19.0-35-generic, x86_64: installed

$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:03.1/0000:2b:00.0 ==
modalias : pci:v000010DEd00001D01sv00001462sd00008C98bc03sc00i00
vendor   : NVIDIA Corporation
model    : GP108 [GeForce GT 1030]
driver   : nvidia-driver-515 - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-525 - distro non-free recommended
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-510 - distro non-free
driver   : nvidia-driver-515-server - distro non-free
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-418-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

Going back to the syslog entry, I don't know which specific kernel module file it is attempting to load; there *are* some nvidia drivers for the current kernel version, but there appear to be a few items missing (comparison of 5.19.0-32 to 5.19.0-35):
```
$ diff <(find /lib/modules/5.19.0-32-generic/ -name '*nvidia*' -printf '%P\n') <(find /lib/modules/5.19.0-35-generic/ -name '*nvidia*' -printf '%P\n')
36,40d35
< kernel/nvidia-525/nvidia-modeset.ko
< kernel/nvidia-525/nvidia.ko
< kernel/nvidia-525/nvidia-drm.ko
< kernel/nvidia-525/nvidia-peermem.ko
< kernel/nvidia-525/bits/nvidia-uvm.o
42d36
< kernel/nvidia-525/bits/nvidia-drm.o
45,46d38
< kernel/nvidia-525/bits/nvidia.o
< kernel/nvidia-525/bits/nvidia-modeset.o
79d70
< kernel/nvidia-525/bits/nvidia-peermem.o
83d73
< kernel/nvidia-525/nvidia-uvm.ko

```

Obviously, I *could* start switching back to Nouveau drivers... reboot... then reinstall the nVidia drivers... but right now I'm reluctant to start changing things without understanding *what* has gone wrong.

---

### Post by peterx14 on 2023-03-02
It looks to me like the nvidia packages that are being "held back" are being held back because of Ubuntu phased-updates?
```
$ apt-cache policy libnvidia-common-525
libnvidia-common-525:
  Installed: 525.78.01-0ubuntu0.22.04.1
  Candidate: 525.85.05-0ubuntu0.22.04.1
  Version table:
     525.85.05-0ubuntu0.22.04.1 500 (phased 20%)
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages
 *** 525.78.01-0ubuntu0.22.04.1 500
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted i386 Packages
        100 /var/lib/dpkg/status
```
..but that doesn't play well with the fact that my Kernel *has* been upgraded. I'm a bit disappointed in Ubuntu/Canonical over this... :(

---

### Post by peterx14 on 2023-03-02
Okay, so I've managed to add a timeout to my grub menu and that has allowed me to boot using the previous kernel (5.19.0-32-generic), and everything is working fine now. But.. I guess I'll need to continue manually selecting this kernel at boot until such time as I'm "allowed" to install the new nvidia packages?

---

### Post by MAFoElffen on 2023-03-02
I have a few machines with NVidia. The problem of new kernels vs. NVidia drivers had been a problem for over a decade, especially with NVidia drivers directly from NVidia. I find that the driver through Ubuntu are more stable and have less problems with them.

What I usually do when this happens is to uninstall the NVidia drivers, and reinstall them. Just a thought.

---

### Post by peterx14 on 2023-03-05
@MAFoElffen - thanks for your reply!
Yeah, nVidia can be a total pain sometimes, but I think in this case it might be more due to Canonical.

Since my previous post, I've just hibernated my PC so I didn't have to deal with this. I've been keeping an eye on apt though... and the "phased-updates" percentage has been changing. Yesterday I got this:
```
$ apt-cache policy libnvidia-common-525
libnvidia-common-525:
  Installed: 525.78.01-0ubuntu0.22.04.1
  Candidate: 525.85.05-0ubuntu0.22.04.1
  Version table:
     525.85.05-0ubuntu0.22.04.1 500 (phased 90%)
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages
 *** 525.78.01-0ubuntu0.22.04.1 500
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted i386 Packages
        100 /var/lib/dpkg/status

```
...but apt upgrade still said it was holding back my nVidia packages, so I assumed I was in the not-included-in-phased-updates-yet-10%. :(

And today, apparently there are no phased updates for this package:
```
$ apt-cache policy libnvidia-common-525
libnvidia-common-525:
  Installed: 525.78.01-0ubuntu0.22.04.1
  Candidate: 525.85.05-0ubuntu0.22.04.1
  Version table:
     525.85.05-0ubuntu0.22.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages
 *** 525.78.01-0ubuntu0.22.04.1 500
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted i386 Packages
        100 /var/lib/dpkg/status

```
...but **still**, apt upgrade is saying it is holding back my nVidia packages, which is... just annoying now.
```
$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libimage-magick-perl imagemagick libdcmtk16 libopenexr25 libmagick++-6.q16-8
  libmagickcore-6.q16-6-extra libimage-magick-q16-perl libmagickwand-6.q16-6
  imagemagick-6.q16 libmagickcore-6.q16-6 imagemagick-6-common
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  gnome-remote-desktop grub-efi-amd64-bin grub-efi-amd64-signed libnvidia-cfg1-525
  libnvidia-compute-525 libnvidia-compute-525:i386 libnvidia-decode-525 libnvidia-decode-525:i386
  libnvidia-encode-525 libnvidia-encode-525:i386 libnvidia-extra-525 libnvidia-fbc1-525
  libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386
  linux-modules-nvidia-525-generic-hwe-22.04 nvidia-compute-utils-525 nvidia-driver-525
  nvidia-kernel-common-525 nvidia-kernel-source-525 nvidia-utils-525 shim-signed
  xserver-xorg-video-nvidia-525
The following packages will be upgraded:
  fonts-opensymbol gir1.2-pango-1.0 libmbim-glib4 libmbim-proxy libmm-glib0 libnvidia-common-525
  libpango-1.0-0 libpango-1.0-0:i386 libpangocairo-1.0-0 libpangocairo-1.0-0:i386 libpangoft2-1.0-0
  libpangoft2-1.0-0:i386 libpangoxft-1.0-0 libqmi-glib5 libqmi-proxy libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-help-common libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze libreoffice-style-colibre
  libreoffice-style-elementary libreoffice-style-yaru libreoffice-writer libsnmp-base libsnmp40
  libuno-cppu3 libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3
  libuno-salhelpergcc3-3 modemmanager ncat nmap nmap-common python3-software-properties python3-uno
  software-properties-common software-properties-gtk tcpdump ubuntu-advantage-tools
  uno-libs-private ure
54 to upgrade, 0 to newly install, 0 to remove and 23 not to upgrade.
Need to get 127 MB of archives.
After this operation, 1,099 kB of additional disk space will be used.
Do you want to continue? [Y/n]

```
I presume there must be some package in there that is still part of a phased upgrade that is a dependency that prevents me getting the updates yet.

---

### Post by #&amp;thj^% on 2023-03-05
I used to think that the repo versions on Nvidia was more trouble free, I don't think that any more.
```
apt policy nvidia-driver
nvidia-driver:
  Installed: (none)
  Candidate: 525.89.02-1
  Version table:
     525.89.02-1 990
        990 http://deb.debian.org/debian sid/non-free amd64 Packages
        990 http://ftp.us.debian.org/debian sid/non-free amd64 Packages
```
This is not a recommend, 
Please try:
```
sudo apt dist-upgrade -s
```
This is a dry run to see what will get pulled in.
see if we can get Nvidia happy with the system again.

---

### Post by peterx14 on 2023-03-05
@1fallen - thanks for your reply!

```

$ sudo apt dist-upgrade -s
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libimage-magick-perl imagemagick libdcmtk16 libopenexr25 libmagick++-6.q16-8
  libmagickcore-6.q16-6-extra libimage-magick-q16-perl libmagickwand-6.q16-6
  imagemagick-6.q16 libmagickcore-6.q16-6 imagemagick-6-common
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages will be REMOVED
  linux-modules-nvidia-525-5.19.0-32-generic
The following NEW packages will be installed
  linux-modules-nvidia-525-5.19.0-35-generic
The following packages have been kept back:
  gnome-remote-desktop grub-efi-amd64-bin grub-efi-amd64-signed shim-signed
The following packages will be upgraded:
  fonts-opensymbol gir1.2-pango-1.0 libmbim-glib4 libmbim-proxy libmm-glib0 libnvidia-cfg1-525
  libnvidia-common-525 libnvidia-compute-525 libnvidia-compute-525:i386 libnvidia-decode-525
  libnvidia-decode-525:i386 libnvidia-encode-525 libnvidia-encode-525:i386 libnvidia-extra-525
  libnvidia-fbc1-525 libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386 libpango-1.0-0
  libpango-1.0-0:i386 libpangocairo-1.0-0 libpangocairo-1.0-0:i386 libpangoft2-1.0-0
  libpangoft2-1.0-0:i386 libpangoxft-1.0-0 libqmi-glib5 libqmi-proxy libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-help-common libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze libreoffice-style-colibre
  libreoffice-style-elementary libreoffice-style-yaru libreoffice-writer libsnmp-base libsnmp40
  libuno-cppu3 libuno-cppuhelpergcc3-3 libuno-purpenvhelpergcc3-3 libuno-sal3
  libuno-salhelpergcc3-3 linux-modules-nvidia-525-generic-hwe-22.04 modemmanager ncat nmap
  nmap-common nvidia-compute-utils-525 nvidia-driver-525 nvidia-kernel-common-525
  nvidia-kernel-source-525 nvidia-utils-525 python3-software-properties python3-uno
  software-properties-common software-properties-gtk tcpdump ubuntu-advantage-tools
  uno-libs-private ure xserver-xorg-video-nvidia-525
73 to upgrade, 1 to newly install, 1 to remove and 4 not to upgrade.
1 standard LTS security update
Inst nvidia-driver-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-extra-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-common-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [all]) []
Inst libnvidia-gl-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) [libnvidia-gl-525:amd64 on libnvidia-gl-525:i386] [libnvidia-gl-525:i386 on libnvidia-gl-525:amd64] [libnvidia-gl-525:i386 ]
Inst libnvidia-gl-525:i386 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386]) []
Inst linux-modules-nvidia-525-generic-hwe-22.04 [5.19.0-32.33~22.04.1] (5.19.0-35.36~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64]) []
Remv linux-modules-nvidia-525-5.19.0-32-generic [5.19.0-32.33~22.04.1] []
Inst nvidia-kernel-common-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst nvidia-kernel-source-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-decode-525:i386 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386]) [libnvidia-decode-525:amd64 on libnvidia-decode-525:i386] [libnvidia-decode-525:i386 on libnvidia-decode-525:amd64] [libnvidia-decode-525:amd64 ]
Inst libnvidia-decode-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-compute-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) [libnvidia-compute-525:amd64 on libnvidia-compute-525:i386] [libnvidia-compute-525:i386 on libnvidia-compute-525:amd64] [libnvidia-compute-525:i386 ]
Inst libnvidia-compute-525:i386 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386]) []
Inst nvidia-compute-utils-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-encode-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) [libnvidia-encode-525:amd64 on libnvidia-encode-525:i386] [libnvidia-encode-525:i386 on libnvidia-encode-525:amd64] [libnvidia-encode-525:i386 ]
Inst libnvidia-encode-525:i386 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386]) []
Inst nvidia-utils-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst xserver-xorg-video-nvidia-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-cfg1-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libnvidia-fbc1-525 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) [libnvidia-fbc1-525:amd64 on libnvidia-fbc1-525:i386] [libnvidia-fbc1-525:i386 on libnvidia-fbc1-525:amd64] [libnvidia-fbc1-525:i386 ]
Inst libnvidia-fbc1-525:i386 [525.78.01-0ubuntu0.22.04.1] (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386]) []
Inst linux-modules-nvidia-525-5.19.0-35-generic (5.19.0-35.36~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst ubuntu-advantage-tools [27.13.5~22.04.1] (27.13.6~22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Inst tcpdump [4.99.1-3build2] (4.99.1-3ubuntu0.1 Ubuntu:22.04/jammy-updates [amd64])
Inst fonts-opensymbol [2:102.12+LibO7.3.7-0ubuntu0.22.04.1] (2:102.12+LibO7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libpangocairo-1.0-0:i386 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [i386]) [libpangocairo-1.0-0:amd64 on libpangocairo-1.0-0:i386] [libpangocairo-1.0-0:i386 on libpangocairo-1.0-0:amd64] [libpangocairo-1.0-0:amd64 ]
Inst libpangocairo-1.0-0 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64]) [gir1.2-pango-1.0:amd64 ]
Inst gir1.2-pango-1.0 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libpangoft2-1.0-0 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64]) [libpangoft2-1.0-0:amd64 on libpangoft2-1.0-0:i386] [libpangoft2-1.0-0:i386 on libpangoft2-1.0-0:amd64] [libpangoft2-1.0-0:i386 libpangoxft-1.0-0:amd64 ]
Inst libpangoft2-1.0-0:i386 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [i386]) [libpangoxft-1.0-0:amd64 ]
Inst libpango-1.0-0:i386 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [i386]) [libpango-1.0-0:amd64 on libpango-1.0-0:i386] [libpango-1.0-0:i386 on libpango-1.0-0:amd64] [libpango-1.0-0:amd64 libpangoxft-1.0-0:amd64 ]
Inst libpango-1.0-0 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64]) [libpangoxft-1.0-0:amd64 ]
Inst libpangoxft-1.0-0 [1.50.6+ds-2] (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Inst libmbim-proxy [1.26.2-1build1] (1.28.0-1~ubuntu20.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libmbim-glib4 [1.26.2-1build1] (1.28.0-1~ubuntu20.04.1 Ubuntu:22.04/jammy-updates [amd64])
Inst libmm-glib0 [1.18.6-1] (1.20.0-1~ubuntu22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Inst libqmi-proxy [1.30.4-1] (1.32.0-1ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libqmi-glib5 [1.30.4-1] (1.32.0-1ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Inst libuno-sal3 [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Inst libuno-salhelpergcc3-3 [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Inst libuno-cppu3 [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Inst libuno-cppuhelpergcc3-3 [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst ure [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst uno-libs-private [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Inst libuno-purpenvhelpergcc3-3 [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Inst libreoffice-calc [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-impress [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-draw [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-math [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-help-en-gb [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all]) []
Inst libreoffice-help-en-us [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all]) []
Inst libreoffice-help-common [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all]) []
Inst libreoffice-common [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all]) []
Inst libreoffice-gnome [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-gtk3 [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-base-core [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) [libreoffice-writer:amd64 ]
Inst python3-uno [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) [libreoffice-writer:amd64 ]
Inst libreoffice-writer [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64]) []
Inst libreoffice-core [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Inst libreoffice-l10n-en-gb [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libreoffice-style-colibre [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libreoffice-style-breeze [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libreoffice-style-elementary [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libreoffice-style-yaru [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libsnmp-base [5.9.1+dfsg-1ubuntu2.4] (5.9.1+dfsg-1ubuntu2.5 Ubuntu:22.04/jammy-updates [all])
Inst libsnmp40 [5.9.1+dfsg-1ubuntu2.4] (5.9.1+dfsg-1ubuntu2.5 Ubuntu:22.04/jammy-updates [amd64])
Inst modemmanager [1.18.6-1] (1.20.0-1~ubuntu22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Inst ncat [7.91+dfsg1+really7.80+dfsg1-2build1] (7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 Ubuntu:22.04/jammy-updates [amd64])
Inst nmap-common [7.91+dfsg1+really7.80+dfsg1-2build1] (7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 Ubuntu:22.04/jammy-updates [all]) [nmap:amd64 ]
Inst nmap [7.91+dfsg1+really7.80+dfsg1-2build1] (7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 Ubuntu:22.04/jammy-updates [amd64])
Inst software-properties-common [0.99.22.4] (0.99.22.6 Ubuntu:22.04/jammy-updates [all]) []
Inst software-properties-gtk [0.99.22.4] (0.99.22.6 Ubuntu:22.04/jammy-updates [all]) []
Inst python3-software-properties [0.99.22.4] (0.99.22.6 Ubuntu:22.04/jammy-updates [all])
Inst libreoffice-ogltrans [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Inst libreoffice-pdfimport [1:7.3.7-0ubuntu0.22.04.1] (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf nvidia-driver-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-extra-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-common-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [all])
Conf libnvidia-gl-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-gl-525:i386 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386])
Conf linux-modules-nvidia-525-generic-hwe-22.04 (5.19.0-35.36~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf nvidia-kernel-common-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf nvidia-kernel-source-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-decode-525:i386 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386])
Conf libnvidia-decode-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-compute-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-compute-525:i386 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386])
Conf nvidia-compute-utils-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-encode-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-encode-525:i386 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386])
Conf nvidia-utils-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf xserver-xorg-video-nvidia-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-cfg1-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-fbc1-525 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-fbc1-525:i386 (525.85.05-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [i386])
Conf linux-modules-nvidia-525-5.19.0-35-generic (5.19.0-35.36~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf ubuntu-advantage-tools (27.13.6~22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf tcpdump (4.99.1-3ubuntu0.1 Ubuntu:22.04/jammy-updates [amd64])
Conf fonts-opensymbol (2:102.12+LibO7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libpangocairo-1.0-0:i386 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [i386])
Conf libpangocairo-1.0-0 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf gir1.2-pango-1.0 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf libpangoft2-1.0-0 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf libpangoft2-1.0-0:i386 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [i386])
Conf libpango-1.0-0:i386 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [i386])
Conf libpango-1.0-0 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf libpangoxft-1.0-0 (1.50.6+ds-2ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf libmbim-proxy (1.28.0-1~ubuntu20.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libmbim-glib4 (1.28.0-1~ubuntu20.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libmm-glib0 (1.20.0-1~ubuntu22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libqmi-proxy (1.32.0-1ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libqmi-glib5 (1.32.0-1ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libuno-sal3 (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libuno-salhelpergcc3-3 (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libuno-cppu3 (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libuno-cppuhelpergcc3-3 (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf ure (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf uno-libs-private (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libuno-purpenvhelpergcc3-3 (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-calc (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-impress (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-draw (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-math (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-help-en-gb (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-help-en-us (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-help-common (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-common (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-gnome (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-gtk3 (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-base-core (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf python3-uno (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-writer (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-core (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [amd64])
Conf libreoffice-l10n-en-gb (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-style-colibre (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-style-breeze (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-style-elementary (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-style-yaru (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libsnmp-base (5.9.1+dfsg-1ubuntu2.5 Ubuntu:22.04/jammy-updates [all])
Conf libsnmp40 (5.9.1+dfsg-1ubuntu2.5 Ubuntu:22.04/jammy-updates [amd64])
Conf modemmanager (1.20.0-1~ubuntu22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf ncat (7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 Ubuntu:22.04/jammy-updates [amd64])
Conf nmap-common (7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 Ubuntu:22.04/jammy-updates [all])
Conf nmap (7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1 Ubuntu:22.04/jammy-updates [amd64])
Conf software-properties-common (0.99.22.6 Ubuntu:22.04/jammy-updates [all])
Conf software-properties-gtk (0.99.22.6 Ubuntu:22.04/jammy-updates [all])
Conf python3-software-properties (0.99.22.6 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-ogltrans (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])
Conf libreoffice-pdfimport (1:7.3.7-0ubuntu0.22.04.2 Ubuntu:22.04/jammy-updates [all])

```
That looks like it would force it though; shall I go for it? I note it'll remove the older nVidia drivers... which is fine as long as the new ones work, but it'd be a pain for me right now if it broke things... but on the other-hand, it all looks fine! :O

---

### Post by #&amp;thj^% on 2023-03-05
yep I would go for it.
@ Canonical my goodness, where oh where did the quality go?
```
inxi -Gz
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 530.30.02
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia resolution:
    1: 1920x1080~120Hz 2: N/A
  API: OpenGL v: 4.6.0 NVIDIA 530.30.02 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2

```

---

### Post by peterx14 on 2023-03-05
Thanks loads - that seems to have fixed it!!

I applied all updates, rebooted and everything is fine:
```
$ uname -a
Linux kafka 5.19.0-35-generic #36~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb 17 15:17:25 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

$ sudo nvidia-smi 
Sun Mar  5 19:15:08 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.85.05    Driver Version: 525.85.05    CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:2B:00.0  On |                  N/A |
| 35%   36C    P0    N/A /  30W |    280MiB /  2048MiB |      4%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      2463      G   /usr/lib/xorg/Xorg                133MiB |
|    0   N/A  N/A      2607      G   /usr/bin/gnome-shell               60MiB |
|    0   N/A  N/A      3871      G   ...836305579612497723,131072       62MiB |
+-----------------------------------------------------------------------------+

$ apt-cache policy libnvidia-common-525
libnvidia-common-525:
  Installed: 525.85.05-0ubuntu0.22.04.1
  Candidate: 525.85.05-0ubuntu0.22.04.1
  Version table:
 *** 525.85.05-0ubuntu0.22.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages
        100 /var/lib/dpkg/status
     525.78.01-0ubuntu0.22.04.1 500
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted i386 Packages

```

Thanks again!! :D

---

### Post by #&amp;thj^% on 2023-03-05
That's Great, thanks for marking as solved.
Other Lookers this may not work for everyone, so :!:Caution:!: is advised

---

### Post by leeninde on 2023-03-09
As an additional note, I was able to use the following to perform the upgrade required. Likely, another way of doing the same thing:
[COLOR=#000000][I]sudo apt full-upgrade

[/I][/COLOR]

---

