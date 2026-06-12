---
title: "New Build of 14.04 doesn't arrive at Login Screen"
date: 2014-10-10
forum: General Help
---

### Post by jamesisin on 2014-10-10
Just built a Lenovo T410s with 64 bit Ubuntu 14.04.1, added some basic stuff (ssh, smb, Opera, Spotify, Clementine), and ran updates.  Upon rebooting it doesn't get past the screen which merely says Ubuntu (and has the five colored dots).  I do hear the Login Screen drum roll and I can ssh into the machine (sure glad I added that before the reboot).

Any help is appreciated.


Thanks,

James

---

### Post by jamesisin on 2014-10-13
Anybody?

---

### Post by sp40140 on 2014-10-13
What are the hardware specs of your machine? specially the video adapter. And what drivers are you using?

---

### Post by jamesisin on 2014-10-13
I have not enabled any third-party drivers, so whatever is chosen by the OS for a T410s of that ilk.  If you'd like me to run specific commands I am able to ssh into the box.

---

### Post by mc4man on 2014-10-13
shows as • Intel® HD Graphics and NVIDIA® NVS3100M Graphics
the intel may be 3000?
You could try booting to recovery > resume.. which will attempt to boot normally without any video driver loaded
If that works then search out issues with Intel HD Graphics 3000 (Sandy Bridge) & 14.04.1

---

### Post by jamesisin on 2014-10-13
That was helpful but we are not done yet.

Going Recovery --> Resume did give me a login screen.  I then logged in and the accoutrements of the login screen left leaving the background.  The desktop never arrived.  The mouse is active but won't interact with the background image (why would it?), and I could probably change to a different tty to get a prompt (but didn't try).

Through an ssh connection I looked at GPU information:

```
lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device [17aa:21be]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
	Memory at f0000000 (64-bit, prefetchable) [size=128M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
	Subsystem: Lenovo Device [17aa:215f]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fc627800 (64-bit, non-prefetchable) [size=16]
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218M [NVS 3100M] [10de:0a6c] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device [17aa:21be]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at cd000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
	Subsystem: Lenovo Device [17aa:218f]


sudo lshw -numeric -C display

  *-display
       description: VGA compatible controller
       product: GT218M [NVS 3100M] [10DE:A6C]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:cc000000-ccffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:2000(size=128) memory:cd000000-cd07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller [8086:46]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fc000000-fc3fffff memory:f0000000-f7ffffff ioport:1800(size=8)
```

---

### Post by sp40140 on 2014-10-13
The blank screen with active mouse is sign of Unity plug-in not running. This is display driver config situation.
Can you try to get to tty and hit "startx" and see if that launches unity for you?
if that doesn't work, get to tty and rename ~/.Xauthority folder to something else. and re-boot the machine. re-booting will re-create that folder.

---

### Post by mc4man on 2014-10-13
If continuing to get stuck - 
Your intel driver apparently isn't loading  *-display UNCLAIMED

Assuming the install worked until you updated attached is full list of 14.04.1 updates on a default install.
Some of the updates may be suspect to your issue, ie. the kernel, xserver-xorg*, ect.
(though the xserver-xorg-video-intel update doesn't mention sandybridge

Have you tried booting to another kernel? (if you did update the kernel, installed is 3.13.0.32.38, update is to 3.13.0.37.44

---

### Post by jamesisin on 2014-10-13
sp40140 - The screen after login is not blank; the desktop image is present.  If I switch my tty to f2 and startx I get a black screen with no mouse.  (I am still able to switch between all the tty's.)

mc4man - I believe you are correct in that I only have two kernels on that machine (32 and 37).  Let me try the first and see where that takes me.

---

### Post by jamesisin on 2014-10-13
Looks to be about the same behavior.  The startx does have a little output before it stops so that may be useful.

Kernel 32 after initializing a bunch of built-in extensions:

```
Loading extension GLX
Loading extension NV-GLX
Loading extension NV-CONTROL
```

Kernel 37 after initializing a bunch of built-in extensions:

```
Loading extension GLX
```

(While attempting to use the Recovery --> Resume under 32 I saw a bunch of "failed to disable graphis turbo" messages in case that is interesting.)

---

### Post by mc4man on 2014-10-13
I thought I saw a thread recently that was very similar, if I stumble across will link (i believe they had hd3000
You could possibly try downgrading some packages but that's risky & somewhat complicated with no login to a session
(gnome-flashback > metacity may work thru recovery > resume

As far as recovery, usually recovery > resume to an ubuntu (unity) session would log you in under llvmpipe, that's not happening for you.
It's possible if you installed nvidia drivers & nvidia-prime that you may get a working session but you'd also get tearing as there is no vsync under nvidia-prime.

A shot in the dark - 
go recovery > fsck > root shell prompt and remove -  (or any other way to remove a package), this isn't needed when using intel
xserver-xorg-video-nouveau
Then reboot normally..

---

### Post by jamesisin on 2014-10-13
What is that package?  I suppose I could just run *sudo apt-get remove xserver-xorg-video-nouveau*, but that seems extreme.

---

### Post by mc4man on 2014-10-13
> **jamesisin said:**
> What is that package?  I suppose I could just run *sudo apt-get remove xserver-xorg-video-nouveau*, but that seems extreme.

Not extreme at all. It has no value when using the Intel drivers & no value I've seen when using nvidia drivers on an optimus laptop. I don't have it installed here on a lenovo Y510P (Haswell HD4600
> doug@doug-Y510P:~$ apt-cache policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: (none)
  Candidate: 1:1.0.10-1ubuntu2
  Version table:
     1:1.0.10-1ubuntu2 0
        500 [http://ubuntu.mirror.constant.com/](http://ubuntu.mirror.constant.com/) trusty/main amd64 Packages


alt. shot in dark, if on a 64 bit install what does this return? - 
```
sudo update-alternatives --display  x86_64-linux-gnu_gl_conf
```
on 32 bit may be this, not really sure - 
sudo update-alternatives --display   i386-linux-gnu_gl_conf

---

### Post by jamesisin on 2014-10-14
Here is that ouput:

```
sudo update-alternatives --display x86_64-linux-gnu_gl_conf

x86_64-linux-gnu_gl_conf - auto mode
  link currently points to /usr/lib/nvidia-331/ld.so.conf
/usr/lib/nvidia-331-prime/ld.so.conf - priority 8603
  slave x86_64-linux-gnu_grub_fb_blacklist: /usr/share/nvidia-331/nvidia-331.grub-gfxpayload
  slave x86_64-linux-gnu_man_nvidiaxconfig.gz: /usr/share/man/man1/alt-nvidia-331-xconfig.1.gz
  slave x86_64-linux-gnu_nvidia-debugdump: /usr/lib/nvidia-331/bin/nvidia-debugdump
  slave x86_64-linux-gnu_nvidia-smi.1.gz: /usr/share/man/man1/alt-nvidia-331-smi.1.gz
  slave x86_64-linux-gnu_nvidia_app_profile: /usr/share/nvidia-331/nvidia-application-profiles-331.38-rc
  slave x86_64-linux-gnu_nvidia_bug_report: /usr/lib/nvidia-331/bin/nvidia-bug-report.sh
  slave x86_64-linux-gnu_nvidia_modconf: /lib/nvidia-331/modprobe.conf
  slave x86_64-linux-gnu_nvidia_smi: /usr/lib/nvidia-331/bin/nvidia-smi
  slave x86_64-linux-gnu_nvidia_xconfig: /usr/lib/nvidia-331/bin/nvidia-xconfig
/usr/lib/nvidia-331/ld.so.conf - priority 8604
  slave x86_64-linux-gnu_grub_fb_blacklist: /usr/share/nvidia-331/nvidia-331.grub-gfxpayload
  slave x86_64-linux-gnu_libvdpau_nvidia.so: /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so
  slave x86_64-linux-gnu_libvdpau_nvidia.so.1: /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so.1
  slave x86_64-linux-gnu_libvdpau_nvidia.so.1_lib32: /usr/lib32/nvidia-331/vdpau/libvdpau_nvidia.so.1
  slave x86_64-linux-gnu_libvdpau_nvidia.so_lib32: /usr/lib32/nvidia-331/vdpau/libvdpau_nvidia.so
  slave x86_64-linux-gnu_man_nvidiaxconfig.gz: /usr/share/man/man1/alt-nvidia-331-xconfig.1.gz
  slave x86_64-linux-gnu_man_persistenced.gz: /usr/share/man/man1/alt-nvidia-331-persistenced.1.gz
  slave x86_64-linux-gnu_nvidia-cuda-mps-control: /usr/lib/nvidia-331/bin/nvidia-cuda-mps-control
  slave x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz: /usr/share/man/man1/alt-nvidia-331-cuda-mps-control.1.gz
  slave x86_64-linux-gnu_nvidia-cuda-mps-server: /usr/lib/nvidia-331/bin/nvidia-cuda-mps-server
  slave x86_64-linux-gnu_nvidia-debugdump: /usr/lib/nvidia-331/bin/nvidia-debugdump
  slave x86_64-linux-gnu_nvidia-smi.1.gz: /usr/share/man/man1/alt-nvidia-331-smi.1.gz
  slave x86_64-linux-gnu_nvidia_app_profile: /usr/share/nvidia-331/nvidia-application-profiles-331.38-rc
  slave x86_64-linux-gnu_nvidia_bug_report: /usr/lib/nvidia-331/bin/nvidia-bug-report.sh
  slave x86_64-linux-gnu_nvidia_drv: /usr/lib/nvidia-331/xorg/nvidia_drv.so
  slave x86_64-linux-gnu_nvidia_modconf: /lib/nvidia-331/modprobe.conf
  slave x86_64-linux-gnu_nvidia_persistenced: /usr/lib/nvidia-331/bin/nvidia-persistenced
  slave x86_64-linux-gnu_nvidia_smi: /usr/lib/nvidia-331/bin/nvidia-smi
  slave x86_64-linux-gnu_nvidia_xconfig: /usr/lib/nvidia-331/bin/nvidia-xconfig
  slave x86_64-linux-gnu_xorg_extra_modules: /usr/lib/nvidia-331/xorg
/usr/lib/x86_64-linux-gnu/mesa/ld.so.conf - priority 500
  slave x86_64-linux-gnu_xorg_extra_modules: /usr/lib/x86_64-linux-gnu/xorg/x11-extra-modules
Current 'best' version is '/usr/lib/nvidia-331/ld.so.conf'.
```

---

### Post by jamesisin on 2014-10-14
Purging removed two packages:

```
sudo apt-get purge xserver-xorg-video-nouveau

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-video-all* xserver-xorg-video-nouveau*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 374 kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 200272 files and directories currently installed.)
Removing xserver-xorg-video-all (1:7.7+1ubuntu8) ...
Removing xserver-xorg-video-nouveau (1:1.0.10-1ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
```

---

### Post by jamesisin on 2014-10-14
No change in behavior after reboot.

---

### Post by mc4man on 2014-10-14
> x86_64-linux-gnu_gl_conf - auto mode
  link currently points to /usr/lib/nvidia-331/ld.so.conf
That would likely be an issue if nvidia drivers & nvidia-prime aren't installed.
Try switching to /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
```
sudo update-alternatives --config  x86_64-linux-gnu_gl_conf
```
Then choose the mesa alt., ect.

Edit: - there may be an add. commands needed after switching, should track down..
```
sudo ldconfig
sudo update-initramfs -u
```

Did you install nvidia drivers?, post says new install, ect.

---

### Post by jamesisin on 2014-10-14
No change.

```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf

There are 3 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).

  Selection    Path                                       Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-331/ld.so.conf              8604      auto mode
  1            /usr/lib/nvidia-331-prime/ld.so.conf        8603      manual mode
  2            /usr/lib/nvidia-331/ld.so.conf              8604      manual mode
  3            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode

Press enter to keep the current choice[*], or type selection number: 3
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode


sudo update-alternatives --display x86_64-linux-gnu_gl_conf

x86_64-linux-gnu_gl_conf - manual mode
  link currently points to /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
/usr/lib/nvidia-331-prime/ld.so.conf - priority 8603
  slave x86_64-linux-gnu_grub_fb_blacklist: /usr/share/nvidia-331/nvidia-331.grub-gfxpayload
  slave x86_64-linux-gnu_man_nvidiaxconfig.gz: /usr/share/man/man1/alt-nvidia-331-xconfig.1.gz
  slave x86_64-linux-gnu_nvidia-debugdump: /usr/lib/nvidia-331/bin/nvidia-debugdump
  slave x86_64-linux-gnu_nvidia-smi.1.gz: /usr/share/man/man1/alt-nvidia-331-smi.1.gz
  slave x86_64-linux-gnu_nvidia_app_profile: /usr/share/nvidia-331/nvidia-application-profiles-331.38-rc
  slave x86_64-linux-gnu_nvidia_bug_report: /usr/lib/nvidia-331/bin/nvidia-bug-report.sh
  slave x86_64-linux-gnu_nvidia_modconf: /lib/nvidia-331/modprobe.conf
  slave x86_64-linux-gnu_nvidia_smi: /usr/lib/nvidia-331/bin/nvidia-smi
  slave x86_64-linux-gnu_nvidia_xconfig: /usr/lib/nvidia-331/bin/nvidia-xconfig
/usr/lib/nvidia-331/ld.so.conf - priority 8604
  slave x86_64-linux-gnu_grub_fb_blacklist: /usr/share/nvidia-331/nvidia-331.grub-gfxpayload
  slave x86_64-linux-gnu_libvdpau_nvidia.so: /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so
  slave x86_64-linux-gnu_libvdpau_nvidia.so.1: /usr/lib/nvidia-331/vdpau/libvdpau_nvidia.so.1
  slave x86_64-linux-gnu_libvdpau_nvidia.so.1_lib32: /usr/lib32/nvidia-331/vdpau/libvdpau_nvidia.so.1
  slave x86_64-linux-gnu_libvdpau_nvidia.so_lib32: /usr/lib32/nvidia-331/vdpau/libvdpau_nvidia.so
  slave x86_64-linux-gnu_man_nvidiaxconfig.gz: /usr/share/man/man1/alt-nvidia-331-xconfig.1.gz
  slave x86_64-linux-gnu_man_persistenced.gz: /usr/share/man/man1/alt-nvidia-331-persistenced.1.gz
  slave x86_64-linux-gnu_nvidia-cuda-mps-control: /usr/lib/nvidia-331/bin/nvidia-cuda-mps-control
  slave x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz: /usr/share/man/man1/alt-nvidia-331-cuda-mps-control.1.gz
  slave x86_64-linux-gnu_nvidia-cuda-mps-server: /usr/lib/nvidia-331/bin/nvidia-cuda-mps-server
  slave x86_64-linux-gnu_nvidia-debugdump: /usr/lib/nvidia-331/bin/nvidia-debugdump
  slave x86_64-linux-gnu_nvidia-smi.1.gz: /usr/share/man/man1/alt-nvidia-331-smi.1.gz
  slave x86_64-linux-gnu_nvidia_app_profile: /usr/share/nvidia-331/nvidia-application-profiles-331.38-rc
  slave x86_64-linux-gnu_nvidia_bug_report: /usr/lib/nvidia-331/bin/nvidia-bug-report.sh
  slave x86_64-linux-gnu_nvidia_drv: /usr/lib/nvidia-331/xorg/nvidia_drv.so
  slave x86_64-linux-gnu_nvidia_modconf: /lib/nvidia-331/modprobe.conf
  slave x86_64-linux-gnu_nvidia_persistenced: /usr/lib/nvidia-331/bin/nvidia-persistenced
  slave x86_64-linux-gnu_nvidia_smi: /usr/lib/nvidia-331/bin/nvidia-smi
  slave x86_64-linux-gnu_nvidia_xconfig: /usr/lib/nvidia-331/bin/nvidia-xconfig
  slave x86_64-linux-gnu_xorg_extra_modules: /usr/lib/nvidia-331/xorg
/usr/lib/x86_64-linux-gnu/mesa/ld.so.conf - priority 500
  slave x86_64-linux-gnu_xorg_extra_modules: /usr/lib/x86_64-linux-gnu/xorg/x11-extra-modules
Current 'best' version is '/usr/lib/nvidia-331/ld.so.conf'.


sudo ldconfig


sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-37-generic


sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done


sudo shutdown -r now

Broadcast message from poplocaladmin@ubun-sea5n-music
	(/dev/pts/3) at 8:59 ...

The system is going down for reboot NOW!
```

---

### Post by jamesisin on 2014-10-15
I killed that build and built it over.  I installed one update at a time until I found the culprit package.  The naughty package is *ubuntu-drivers-common*.  Does this help us?

---

### Post by Bashing-om on 2014-10-17
jamesisin; Hello;

Pardon me if I am butting in here. But, with Intel and Nvidia graphics what I have seen recommended is 
BumbleBee:
[https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee)

OR
Nvidia-prime:
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

"www.webupd8.org" has a good explanation of what is not going on.

[INDENT][INDENT]Hope my little bit helps
[/INDENT][/INDENT]

---

