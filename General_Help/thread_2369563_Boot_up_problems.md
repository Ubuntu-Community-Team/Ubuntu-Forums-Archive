---
title: "Boot up problems"
date: 2017-08-24
forum: General Help
---

### Post by hardcoretexan on 2017-08-24
I recently installed a new hard drive and installed only Ubuntu 16.04 on it and everything worked fine except the boot, I always have to go to advanced options, pick the latest updated version and then boot up, same thing I have to do with my other laptop that runs linux lite.
But twice in 2 weeks I had to boot with my ubuntu disc into try mode and repair my boot menu. Recently my computer is running very slow and videos are slow and choppy also.
I have only been using Linux/ubuntu for a year or so now so I don't know how to scan for viruses or do a checkup of my system. 

Any idea or help would be appreciated.

Greg

Ubuntu 16.04
HP-625
Processor AMD Athlon(tm) ii P340 Dual-Core Processor x2
Graphics Gallium 0.4 on AMD RS880 (DRM 2.49.0/ 4.10.0-32-generic, LLVM 3.8.0)
Memory 2.7GIB
OS type 64 bit

---

### Post by oldfred on 2017-08-24
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

What video? & what video driver are you using?

Also post these to narrow down where issue may be:

 systemd-analyze 
systemd-analyze critical-chain
systemd-analyze blame

---

### Post by hardcoretexan on 2017-08-24
When I tried to post the report online I got an error saying unrecognizable charachters, but I was able to copy it.


== /sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0 ==
modalias : pci:v000014E4d00004727sv0000103Csd0000145Cbc02sc80i00
vendor   : Broadcom Corporation
model    : BCM4313 802.11bgn Wireless Network Adapter
driver   : bcmwl-kernel-source - distro non-free

== cpu-microcode.py ==
driver   : amd64-microcode - distro non-free

sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS880M [Mobility Radeon HD 4225/4250]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff ioport:5000(size=256) memory:d4300000-d430ffff memory:d4200000-d42fffff memory:c0000-dffff

ubuntu@ubuntu:~$ systemd-analyze 
Startup finished in 50.203s (kernel) + 50.303s (userspace) = 1min 40.506s
ubuntu@ubuntu:~$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @49.752s
&#9492;&#9472;multi-user.target @49.752s
  &#9492;&#9472;getty.target @47.986s
    &#9492;&#9472;getty@tty1.service @47.986s
      &#9492;&#9472;rc-local.service @47.968s +5ms
        &#9492;&#9472;network.target @47.950s
          &#9492;&#9472;NetworkManager.service @19.498s +28.451s
            &#9492;&#9472;dbus.service @16.272s
              &#9492;&#9472;basic.target @16.267s
                &#9492;&#9472;sockets.target @16.267s
                  &#9492;&#9472;snapd.socket @16.263s +3ms
                    &#9492;&#9472;sysinit.target @16.260s
                      &#9492;&#9472;apparmor.service @8.845s +7.389s
                        &#9492;&#9472;local-fs.target @8.844s
                          &#9492;&#9472;tmp.mount @8.836s +6ms
                            &#9492;&#9472;local-fs-pre.target @8.818s
                              &#9492;&#9472;lvm2-monitor.service @2.309s +6.508s
                                &#9492;&#9472;lvm2-lvmetad.service @7.844s
                                  &#9492;&#9472;lvm2-lvmetad.socket @2.308s
                                    &#9492;&#9472;-.slice @1.702s
ubuntu@ubuntu:~$ systemd-analyze blame 
         48.708s dev-sda5.device
         48.088s dev-sr0.device
         48.075s dev-loop0.device
         33.481s snapd.autoimport.service
         28.451s NetworkManager.service
         27.083s ModemManager.service
         21.125s accounts-daemon.service
         15.887s lightdm.service
         14.632s thermald.service
         13.951s networking.service
         12.561s rsyslog.service
         10.632s avahi-daemon.service
         10.342s irqbalance.service
          9.097s systemd-logind.service
          7.389s apparmor.service
          6.508s lvm2-monitor.service
          6.456s ondemand.service
          5.930s systemd-modules-load.service
          5.847s ubiquity.service
          5.590s keyboard-setup.service
          5.450s gpu-manager.service
          5.425s console-setup.service
          5.408s grub-common.service

---

### Post by oldfred on 2017-08-24
Do not know AMD video & issues.
But have seen where using 14.04 and Radeon often better, but they are updating open source drivers to resolve issues.

       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx) 
    
       Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

---

### Post by hardcoretexan on 2017-08-24
So I need to wait until they update the Drivers?

---

### Post by oldfred on 2017-08-24
I do not know why these take so long.
But I do not know LVM, do you have full drive encryption, and slow drive so it is slow un-encrypting drive? And is DVD/CD still in drive, that can slow loading.

48.708s dev-sda5.device
         48.088s dev-sr0.device
         48.075s dev-loop0.device
         33.481s snapd.autoimport.service

---

