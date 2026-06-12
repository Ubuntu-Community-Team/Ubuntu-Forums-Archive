---
title: "After Latest Security Update I Cannot Boot Says Kernel 6.01?"
date: 2023-01-19
forum: General Help
---

### Post by scpatl4now on 2023-01-19
The only way to boot is to go to recovery mode and purge Nvidia drivers.  When I am able to boot I try to install the latest drivers.  I ran a boot repair report

Under host hardware it shows

```
CPU architecture: 64-bit
Video: GP107 [GeForce GTX 1050 Ti] from NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.1.0-1004-oem root=UUID=ccffdd90-935d-4e7a-9cc8-3f5c671834a5 ro recovery nomodeset dis_ucode_ldr
df -Th / : /dev/nvme0n1p1 ext4  484G   45G  414G  10% /

```

```
nvme0n1p1/boot/grub/grub.cfg (filtered)
Ubuntu   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 6.1.0-1004-oem   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 6.0.0-1010-oem   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 5.17.0-1026-oem   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 5.15.0-1027-oracle   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 5.15.0-1023-intel-iotg   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 5.15.0-58-lowlatency   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
Ubuntu, with Linux 5.15.0-58-generic   ccffdd90-935d-4e7a-9cc8-3f5c671834a5
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

```

Is it trying to run an unreleased kernel???  I have not done anything other that run software updates that come through every day (if there are updates).  I just know that if the system reboots I will have to purge nvidia drivers and reinstall them to log in.
Full paste bin
[https://paste.ubuntu.com/p/fPz4WfKhCh/](https://paste.ubuntu.com/p/fPz4WfKhCh/)

---

### Post by scpatl4now on 2023-01-19
Since I figured someone would ask me to do this I ran it to list kernels...what is the Oracle kernel doing there?  Also, I  see  6.0 or 6.1 at the bottom of the list

```
dpkg -l | grep linux-image
rc  linux-image-5.11.0-25-generic                               5.11.0-25.27~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-27-generic                               5.11.0-27.29~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-34-generic                               5.11.0-34.36~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-36-generic                               5.11.0-36.40~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-37-generic                               5.11.0-37.41~20.04.2                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-38-generic                               5.11.0-38.42~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-40-generic                               5.11.0-40.44~20.04.2                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-41-generic                               5.11.0-41.45~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-43-generic                               5.11.0-43.47~20.04.2                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-44-generic                               5.11.0-44.48~20.04.2                                 amd64        Signed kernel image generic
rc  linux-image-5.11.0-46-generic                               5.11.0-46.51~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-25-generic                               5.13.0-25.26~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-27-generic                               5.13.0-27.29~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-28-generic                               5.13.0-28.31~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-30-generic                               5.13.0-30.33~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-35-generic                               5.13.0-35.40~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-37-generic                               5.13.0-37.42~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-39-generic                               5.13.0-39.44~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-40-generic                               5.13.0-40.45~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-41-generic                               5.13.0-41.46~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-44-generic                               5.13.0-44.49~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-48-generic                               5.13.0-48.54~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-51-generic                               5.13.0-51.58~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.13.0-52-generic                               5.13.0-52.59~20.04.1                                 amd64        Signed kernel image generic
ii  linux-image-5.15.0-1023-intel-iotg                          5.15.0-1023.28                                       amd64        Signed kernel image intel-iotg
ii  linux-image-5.15.0-1027-oracle                              5.15.0-1027.33                                       amd64        Signed kernel image oracle
rc  linux-image-5.15.0-41-generic                               5.15.0-41.44~20.04.1                                 amd64        Signed kernel image generic
rc  linux-image-5.15.0-43-generic                               5.15.0-43.46                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-46-generic                               5.15.0-46.49                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-47-generic                               5.15.0-47.51                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-48-generic                               5.15.0-48.54                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-50-generic                               5.15.0-50.56                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-52-generic                               5.15.0-52.58                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-53-generic                               5.15.0-53.59                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-56-generic                               5.15.0-56.62                                         amd64        Signed kernel image generic
rc  linux-image-5.15.0-57-generic                               5.15.0-57.63                                         amd64        Signed kernel image generic
ii  linux-image-5.15.0-58-generic                               5.15.0-58.64                                         amd64        Signed kernel image generic
ii  linux-image-5.15.0-58-lowlatency                            5.15.0-58.64                                         amd64        Signed kernel image lowlatency
ii  linux-image-5.17.0-1026-oem                                 5.17.0-1026.27                                       amd64        Signed kernel image OEM
rc  linux-image-5.4.0-42-generic                                5.4.0-42.46                                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic                                5.4.0-52.57                                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic                                5.4.0-53.59                                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-54-generic                                5.4.0-54.60                                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic                                5.4.0-56.62                                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic                                5.4.0-58.64                                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic                                5.4.0-59.65                                          amd64        Signed kernel image generic
rc  linux-image-5.8.0-34-generic                                5.8.0-34.37~20.04.2                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-36-generic                                5.8.0-36.40~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-38-generic                                5.8.0-38.43~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-40-generic                                5.8.0-40.45~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-41-generic                                5.8.0-41.46~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic                                5.8.0-43.49~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-44-generic                                5.8.0-44.50~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-45-generic                                5.8.0-45.51~20.04.1+1                                amd64        Signed kernel image generic
rc  linux-image-5.8.0-48-generic                                5.8.0-48.54~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-49-generic                                5.8.0-49.55~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-50-generic                                5.8.0-50.56~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-53-generic                                5.8.0-53.60~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-55-generic                                5.8.0-55.62~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-59-generic                                5.8.0-59.66~20.04.1                                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-63-generic                                5.8.0-63.71~20.04.1                                  amd64        Signed kernel image generic
ii  linux-image-6.0.0-1010-oem                                  6.0.0-1010.10                                        amd64        Signed kernel image OEM
ii  linux-image-6.1.0-1004-oem                                  6.1.0-1004.4                                         amd64        Signed kernel image OEM
ii  linux-image-generic                                         5.15.0.58.56                                         amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04                               5.15.0.58.56                                         amd64        Generic Linux kernel image
```

---

### Post by MAFoElffen on 2023-01-19
That is quite a collection of kernels... Why? Are you testing kernels?
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -d
Description:    Ubuntu 22.04.1 LTS

mafoelffen@Mikes-ThinkPad-T520:~$ uname -r
5.15.0-58-generic

mafoelffen@Mikes-ThinkPad-T520:~$ apt list --installed nvidia-*
Listing... Done
nvidia-compute-utils-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-cuda-gdb/jammy,now 11.5.114~11.5.1-1ubuntu1 amd64 [installed,auto-removable]
nvidia-cuda-toolkit-doc/jammy,jammy,now 11.5.1-1ubuntu1 all [installed,auto-removable]
nvidia-driver-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.1 amd64 [installed]
nvidia-kernel-common-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-kernel-source-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.1 amd64 [installed,automatic]
nvidia-opencl-dev/jammy,now 11.5.1-1ubuntu1 amd64 [installed,auto-removable]
nvidia-prime/jammy,jammy,now 0.8.17.1 all [installed,automatic]
nvidia-settings/unknown,now 525.60.13-0ubuntu1 amd64 [installed,automatic]
nvidia-utils-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.1 amd64 [installed,automatic]

mafoelffen@Mikes-ThinkPad-T520:~$ echo $DESKTOP_SESSION
gnome-xorg
m
```

---

### Post by scpatl4now on 2023-01-19
I don't install any kernels other than what is offered with updates.  I do have virtualbox installed if that makes any difference

---

### Post by #&amp;thj^% on 2023-01-19
[s]Someone needs to find why Ubuntu Core Developers are pushing this kernel on unsuspecting users.[/s]
EDIT: see post #7
I can see no obvious reason for this.
> **scpatl4now said:**
>  I do have virtualbox installed if that makes any difference
That might, and just a guess on my part be why.
Bare in mind this is a pure debian install:
```
apt policy virtualbox
virtualbox:
  Installed: 7.0.4-dfsg-5+b1
  Candidate: 7.0.4-dfsg-5+b1
  Version table:
 *** 7.0.4-dfsg-5+b1 100
        100 /var/lib/dpkg/status
     7.0.4-1kaisen 500
        500 https://deb.kaisenlinux.org kaisen-rolling/contrib amd64 Packages


```
No where did I see an oracle-kernel needed, this has to a Ubuntu thing. :)

---

### Post by Impavidus on 2023-01-19
You do have kernels that aren't normally offered through regular updates. Which release of Ubuntu do you run? I suspect 22.04, but I want to be sure.

All those lines starting with rc aren't really interesting. Those are removed kernels that haven't been purged. You can filter them out of the output by piping it through grep again:```
 commands | grep -v '^rc'
```That shows all lines that don't start with rc.

You've got the linux-image-generic package, which is normal and pulls in the linux-image-5.15.0-58-generic kernal package. The others```
linux-image-5.15.0-1023-intel-iotg
linux-image-5.15.0-1027-oracle
linux-image-5.15.0-58-lowlatency
linux-image-5.17.0-1026-oem
linux-image-6.0.0-1010-oem
linux-image-6.1.0-1004-oem
```must have been added somehow. If you buy a computer with Ubuntu preinstalled, you sometimes get such additional kernels. The lowlatency kernel is normally used with Ubuntu Studio (if that's still the case). I don't know what pulls those packages in.

Can you use the grub menu to boot one of the other kernels without fighting nvidia drivers?

---

### Post by ajgreeny on 2023-01-19
There have been a few comments in the forum recently about these unexpected and usually unwanted kernels which seem to have been "forced" into the system by the presence of an nvidia driver; do you use nvidia graphics?

See [https://ubuntuforums.org/showthread.php?t=2482558](https://ubuntuforums.org/showthread.php?t=2482558) for one of these similar oracle kernel threads.

---

### Post by #&amp;thj^% on 2023-01-19
> **ajgreeny said:**
> There have been a few comments in the forum recently about these unexpected and usually unwanted kernels which seem to have been "forced" into the system by the presence of an nvidia driver; do you use nvidia graphics?
.

Are you sure nvidia-driver was the culprit? Just a friendly inquiry is all. :)
I haven't gotten a positive from the OP in that link you showed.

---

### Post by ajgreeny on 2023-01-19
Not sure about that at all, and I've never used an nvidia graphic system in any computer I've owned but the link shown by one-for-tea post #14 in the thread from my link at #7 above points to someone who seems to have found that to be so.

---

### Post by #&amp;thj^% on 2023-01-19
> **ajgreeny said:**
> Not sure about that at all, and I've never used an nvidia graphic system in any computer I've owned but the link shown by one-for-tea post #14 in the thread from my link at #7 above points to someone who seems to have found that to be so.

You was spot on>>>Nvidia, saga continues ;)

---

### Post by grahammechanical on 2023-01-19
I am using my install of Ubuntu 23.04 development version. The latest kernel is 5.19.0.23-generic. I do not understand how the OP got the 6.0 kernel? These release candidate kernels have to be downloaded through a PPA and compiled. According to the Development Section of this forum compilation of these kernels has been failing.

[https://ubuntuforums.org/showthread.php?t=2479685](https://ubuntuforums.org/showthread.php?t=2479685)

Some years ago I experimented with compiling the latest kernels. I gave up because (in part) they did not work with Nvidia proprietary drivers. It seems that is still the case. 

Regards

---

### Post by scpatl4now on 2023-01-20
As it turned out...I just ended up doing a clean install of 22.10 because it seemed easier than to keep trying to troubleshoot what was going on.  I have no idea how to even compile a kernel by my self, so that wouldn't be an option.  Not only did I have 6.0 installed somehow, but also  6.01.  I was running Nvidia graphics (525 driver).  As far as technical knowhow I would say I am about at the midway mark, but after many years I don't do a lot on the tinkering I used to.  I install the updates, and use the PC.  It's been quite a long time since I had a problem like this, but while looking around, I observed lots of people whose systems broke after yesterdays update, and many also had kernel 6 so something went wrong somewhere.

---

### Post by #&amp;thj^% on 2023-01-20
Smart, just avoid the headaches of trying to fix it.
It would help here tremendously if you said you re-installed Nvidia again.
```
nvidia-smi
```
Just for info here I had no problems, but I run a bit differently than most here.(Not a suggestion, just info provided)
```
 inxi -Gz
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 525.85.05
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.6 driver: N/A resolution:
    1: 1920x1080~120Hz 2: 4096x2160~60Hz
  API: OpenGL v: 4.6.0 NVIDIA 525.85.05 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2


me on Fri Jan 20 at 10:15 AM in ~ branch: (HEAD) 
>> uname -r
6.2.0-060200rc4-generic

```

---

### Post by scpatl4now on 2023-01-23
I had to purge and reinstall the nvidia drivers every time the PC booted or I would end up stuck at a blank screen.  I would have liked to know how on earth kernel 6 ended up on my PC, but I needed to have a system that I could use and had work that needed to get done so time really wasn't a luxury I had

---

