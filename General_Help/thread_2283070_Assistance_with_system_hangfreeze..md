---
title: "Assistance with system hang/freeze."
date: 2015-06-18
forum: General Help
---

### Post by mike-bean-heyns on 2015-06-18
Asrock Q2900-ITX with an RTL2832u

I have installed 15.04 and updated. Running 3.19.0-21-generic.
 I installed Kodi and tvheadend as well as ubuntu-restricted-extras.

After a few minutes of watching TV, the entire system will freeze. The only relevant log output I could find is:
```
Jun 19 14:23:43 Heyns-HTPC kernel: [   10.330935] show_signal_msg: 39 callbacks suppressed
Jun 19 14:23:43 Heyns-HTPC kernel: [   10.330946] PVRManager[1212]: segfault at 18 ip 00007fecdf6fe929 sp 00007feca67fb430 error 4 in libc-2.21.so[7fecdf67d000+1c0000]
```

Any advice as to what this means? I had the same problem on Arch Linux with Kernel 4.0.5.

I could work around it by using the 3.14.44 LTS kernel. Is it possible to install this kernel on Vivid?

---

### Post by dino99 on 2015-06-19
pvrmanager has issue : [http://kodi.wiki/view/NextPVR](http://kodi.wiki/view/NextPVR)
[http://linuxcentre.net/getiplayer/get_iplayer-pvr-manager](http://linuxcentre.net/getiplayer/get_iplayer-pvr-manager)
try with the recommended ppa : [https://github.com/get-iplayer/get_iplayer/wiki/ubuntu](https://github.com/get-iplayer/get_iplayer/wiki/ubuntu)

you indeed can install the kernel you wish ; from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) download the 2 headers + 2 images of the selected kernel to an empty folder, then from that folder, run > sudo dpkg -i * , that it

---

### Post by Bucky Ball on 2015-06-19
> **dino99 said:**
> pvrmanager has issue : [http://kodi.wiki/view/NextPVR](http://kodi.wiki/view/NextPVR)

What has this got to do with it???

> NextPVR is a free Personal Video Recorder (PVR) application _for Microsoft Windows._ 

... from your link. In fact, first line.

> **mike-bean-heyns said:**
> 

I could work around it by using the 3.14.44 LTS kernel. Is it possible to install this kernel on Vivid?

Will it work on the 14.04 LTS kernel, 3.13.0-**? If so, perhaps install 14.04 LTS. That is supported until April 2019. 15.04 is supported until late January next year. 

[Tons of links]("https://duckduckgo.com/?q=install+kernel+3.14+in+15.04") on installing that kernel in 14.04, unsure how wise it would be to go backward from the 15.04 kernel, though. You may be able to downgrade just the bits you need, though ...

---

