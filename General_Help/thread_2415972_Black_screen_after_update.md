---
title: "Black screen after update"
date: 2019-04-03
forum: General Help
---

### Post by 2CV67 on 2019-04-03
Hi!

My wife's EeePC Netbook has been dual-booting Ubuntu since 2011 & Ubuntu 16.04LTS since January 2019.

Following an update this morning (including kernel 4.4.0.145.153) it now boots to a black screen.
In detail, after the usual grub screen, then a dark purple screen, I get a completely black screen with no invite cursor or mouse pointer.
The login screen never shows, but if I wait for the disc-activity light to stop, then input my password & enter, then there is lots more disc-activity, showing it is not freezing & the desktop is being set up, but the screen stays black.
I have to use REISUO to exit.
Selecting "Recovery Mode" brings plenty of text but then a black screen again.

Selecting the previous kernel (4.4.0.142.148) from the grub screen brings a normal login screen & normal working.

I used Grub Customizer to prioritize that previous kernel, so now have a working netbook.

But the question is:
Do I now have to stick permanently with that old kernel, or can I expect the next update to fix the problem, or (most likely) should I try to troubleshoot the new kernel?
How?

Thanks for any advice!

---

### Post by 2CV67 on 2019-06-10
I tried to update again - this time to kernel 4.4.0.150.158 - and got the same result:
- Screen stays black after grub screen
- If I wait for disk activity to stop, then enter my p/w & 'Enter' then there is lots of new disk activity, showing desktop being set up, but screen stays black.

Using Grub Customizer to put kernel 4.4.0.142.148 at the top of the grub screen, allows me to get back to normal, but it looks like I can never update again...

I would really appreciate any useful suggestions!

Thanks!

---

### Post by Rubi1200 on 2019-06-10
Hi,

When you use the kernel that boots normally please post the output of the following commands:

```
journalctl -b
```

```
systemd-analyze blame
```

If not already installed, then add:

```
sudo apt install inxi
```

then output of this:

```
inxi -Fzr
```

Please post output with code tags for easier reading.

Thanks.

---

### Post by 2CV67 on 2019-06-10
Thanks for your interest, Rubi1200!

Here are the outputs of your codes:```

chris@Netbk:~$ journalctl -b
-- Logs begin at lun. 2019-06-10 13:32:47 CEST, end at lun. 2019-06-10 15:34:20 
juin 10 13:32:47 Netbk systemd-journald[206]: Runtime journal (/run/log/journal/
juin 10 13:32:47 Netbk kernel: Initializing cgroup subsys cpuset
juin 10 13:32:47 Netbk kernel: Initializing cgroup subsys cpu
juin 10 13:32:47 Netbk kernel: Initializing cgroup subsys cpuacct
juin 10 13:32:47 Netbk kernel: Linux version 4.4.0-142-generic (buildd@lgw01-amd
juin 10 13:32:47 Netbk kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-142-
juin 10 13:32:47 Netbk kernel: KERNEL supported cpus:
juin 10 13:32:47 Netbk kernel:   Intel GenuineIntel
juin 10 13:32:47 Netbk kernel:   AMD AuthenticAMD
juin 10 13:32:47 Netbk kernel:   Centaur CentaurHauls
juin 10 13:32:47 Netbk kernel: x86/fpu: Legacy x87 FPU detected.
juin 10 13:32:47 Netbk kernel: e820: BIOS-provided physical RAM map:
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x000000000009fc00-0x000000000009
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000f
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x0000000000100000-0x000000003f67
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x000000003f680000-0x000000003f68
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x000000003f68e000-0x000000003f6c
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x000000003f6d0000-0x000000003fff
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0
juin 10 13:32:47 Netbk kernel: BIOS-e820: [mem 0x00000000fff00000-0x00000000ffff
juin 10 13:32:47 Netbk kernel: NX (Execute Disable) protection: active
lines 1-23
____________________________________
chris@Netbk:~$ systemd-analyze blame
         15.372s NetworkManager-wait-online.service
         14.580s dev-sda6.device
         10.031s fwupd.service
          8.477s networking.service
          7.394s lightdm.service
          6.931s apparmor.service
          6.575s irqbalance.service
          6.409s apport.service
          5.799s accounts-daemon.service
          5.569s nmbd.service
          5.533s winbind.service
          5.219s NetworkManager.service
          5.045s samba-ad-dc.service
          4.975s grub-common.service
          4.322s systemd-udevd.service
          4.223s gpu-manager.service
          3.806s systemd-logind.service
          3.527s rsyslog.service
          3.524s pppd-dns.service
          3.275s ondemand.service
          2.803s speech-dispatcher.service
          2.402s console-setup.service
          1.770s systemd-rfkill.service
lines 1-23
______________________________________
chris@Netbk:~$ inxi -Fzr
System:    Host: Netbk Kernel: 4.4.0-142-generic x86_64 (64 bit)
           Desktop: Unity 7.4.5  Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK (portable) product: 1015PE v: x.x
           Mobo: ASUSTeK model: 1015PE v: x.xx
           Bios: American Megatrends v: 0801 date: 10/06/2010
CPU:       Single core Intel Atom N455 (-HT-) cache: 512 KB 
           clock speeds: max: 1667 MHz 1: 1667 MHz 2: 1667 MHz
Graphics:  Card: Intel Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1024x600@60.00hz
           GLX Renderer: Mesa DRI Intel Pineview M
           GLX Version: 1.4 Mesa 18.0.5
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-142-generic
Network:   Card-1: Qualcomm Atheros AR8132 Fast Ethernet driver: atl1c
           IF: eth0 state: down mac: <filter>
           Card-2: Ralink RT3090 Wireless 802.11n 1T/1R PCIe driver: rt2800pci
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 250.1GB (40.3% used)
           ID-1: /dev/sda model: ST9250315AS size: 250.1GB
Partition: ID-1: / size: 114G used: 92G (85%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 2.10GB used: 0.58GB (28%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 67.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial main restricted
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial main restricted
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial universe
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial universe
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial-updates universe
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-updates universe
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial multiverse
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial multiverse
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
           deb http://fr.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
           deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu xenial-security main restricted
           deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
           deb http://security.ubuntu.com/ubuntu xenial-security universe
           deb-src http://security.ubuntu.com/ubuntu xenial-security universe
           deb http://security.ubuntu.com/ubuntu xenial-security multiverse
           deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
           Active apt sources in file: /etc/apt/sources.list.d/danielrichter2007-grub-customizer-trusty.list
           deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial main # disabled on upgrade to xenial
Info:      Processes: 208 Uptime: 19 min Memory: 619.7/982.3MB
           Client: Shell (bash) inxi: 2.2.35 
chris@Netbk:~$ 
```

---

### Post by dino99 on 2019-06-10
If it was well working with a prior kernel, then the updated kernel is faulty: missing module ? not supporting the video codec ?
Boot with a working kernel, then grab error via 'journalctl -b' (scroll to the end; errors are usually not seen on top)

An old howto pin to intel_drv.so (maybe some hardware has been deprecated from recent kernels)
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

---

### Post by Rubi1200 on 2019-06-10
@ dino99 output of journalctl -b was posted above.

I do not see any obvious errors there but perhaps you can see something I do not.

@ 2CV67

I suspect the graphics card is not supported on the newer kernels you tried but only on the older one.

However, let's wait and see what dino99 thinks as well as others.

---

### Post by 2CV67 on 2019-06-10
Thanks again, both!

I thought there must be some incompatibility between the graphics card & the latest 2 kernels, but in that case I would expect to see a lot more people complaining on forums etc, and that doesn't seem to be the case...

I did a lot of searching & reading (but not much understanding!)

Among the suggestions, I tried on the .150 kernel:
- Editing the grub line with "nomodeset" - no effect
- Editing grub line by deleting "splash" - no effect
- Recovery modes from Grub - initial verbose output then black screen
- Ctr + Alt + F1-12 - nothing...

---

### Post by 2CV67 on 2019-06-12
So - no more updates in future for my old Netbook then?

No way to get even rough screen function back?
I am happy to re-try anything I already did, if there are any suggestions...

---

### Post by Rubi1200 on 2019-06-12
I don't know if no more kernel updates, perhaps a future one?

I do not know what more you can try but hopefully someone else has some suggestions.

---

### Post by cruzer001 on 2019-06-12
I have seen other reports in this forum concerning the last two kernel upgrades, but its doesn't look to be wide spread.  I think there is a kernel regression going on and a good idea to file a launchpad bug.
```
ubuntu-bug linux
```
Usually launchpad will ask you to try the latest stable (5.x) kernel.

---

### Post by 2CV67 on 2019-06-12
Thanks cruzer001, but I can only run the "ubuntu-bug linux" code in kernel .142 as there is no screen in the problem kernels .145 & .150. 
So Apport never sees anything about the problem!

The procedure for reporting a bug directly on Launchpad is way beyond me...

---

### Post by cruzer001 on 2019-06-12
> 
The procedure for reporting a bug directly on Launchpad is way beyond me... 
I always thought of it as simple when using terminal.  Needed information will be bundled and auto sent to launchpad and you have a few questions to answer.  Thats it, you do need a launchpad account.

I would of thought you could of gone to console (ctrl+alt+f1) with the troubled kernel, but your choice.

Later :)

---

### Post by 2CV67 on 2019-06-14
> **cruzer001 said:**
> I would of thought you could of gone to console (ctrl+alt+f1) with the troubled kernel, but your choice.
Thanks, but it was not my choice!
As I said in post #7 - Ctrl+Alt+F1=black screen so can't do anything.
Same for Ctrl+Alt+F2-12...

---

### Post by Rubi1200 on 2019-06-14
You can also report bugs directly online (you may need to create an account):
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by 2CV67 on 2019-06-14
Yes, I already have an account, but I usually found the process too complicated.

I will try again...

---

### Post by Rubi1200 on 2019-06-14
I must admit I have never reported a bug on Launchpad. However, it might be worthwhile doing so in this case if you have the time and inclination to do so.

---

### Post by 2CV67 on 2019-06-14
Reported bug:
[https://bugs.launchpad.net/ubuntu/+bug/1832863](https://bugs.launchpad.net/ubuntu/+bug/1832863)

While there, I saw a recommendation to update BIOS before reporting kernel bugs, but I don't dare to try that yet...

---

### Post by topoignaz on 2019-10-27
After updating from kernel 4.4.0.142 to 4.4.0.148, I experience exactly the same issue described by the OP on my EeePC 1005HA. 

Please do not deprecate netbook hardware: after their big outcome between 2008 and 2013, their production was discontinued without any real replacement, many people are still using them.

---

### Post by 2CV67 on 2019-11-22
I wiped my Ubuntu partition & installed Lubuntu 18.04.3 instead.
It is working perfectly with latest kernels.

Call this SOLVED, though without finding the reason...

---

