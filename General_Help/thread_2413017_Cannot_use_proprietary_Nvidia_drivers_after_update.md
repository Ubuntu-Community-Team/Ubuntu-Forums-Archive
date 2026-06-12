---
title: "Cannot use proprietary Nvidia drivers after update (14.04)"
date: 2019-02-20
forum: General Help
---

### Post by user9992 on 2019-02-20
Hello,

Last Friday (February 15), everything was working fine.

Then, on Monday (February 18), I encountered a problem when booting: the login screen resolution was very low (1024x768 I think), and I couldn't login, it would just bring me back to the login screen.
I tried booting on a few previous kernel versions, to no avail.

I was able to use a terminal (Ctrl+Alt+F1).
I tried renaming ~/.Xauthority to something else, but it didn't help.

Uninstalling all the Nvidia packages with **apt-get remove** helped a little: I could login, but the resolution was still limited to 1024x768, with no way to change it (at least in the GUI). Of course, it was using the "Nouveau" driver.
Re-installing nvidia-340 prevented me to login again.

Eventually, I removed all the Nvidia packages with ```
sudo apt-get purge nvidia-*
```
It allowed me to login, and to get the correct resolution (1920x1080).

So, I'm currently using the "Nouveau" driver.
However, whenever I try to switch back to nvidia-340 or nvidia-384, the problem comes back.

I'm on Ubuntu 14.04 with an Nvidia GT630.

Here's what got updated/installed last friday (from /var/log/apt/history.log):
> 
Start-Date: 2019-02-15  09:23:37
Commandline: aptdaemon role='role-commit-packages' sender=':1.99'
Upgrade: shim-signed:amd64 (1.33.1~14.04.3+13-0ubuntu2, 1.33.1~14.04.4+13-0ubuntu2), dkms:amd64 (2.2.0.3-1.1ubuntu5.14.04.9, 2.2.0.3-1.1ubuntu5.14.04.10), libssh2-1:amd64 (1.4.3-2ubuntu0.1, 1.4.3-2ubuntu0.2)
End-Date: 2019-02-15  09:40:34

Start-Date: 2019-02-15  09:45:36
Commandline: apt-get install cpufrequtils
Install: cpufrequtils:amd64 (008-1), libcpufreq0:amd64 (008-1, automatic)
End-Date: 2019-02-15  09:45:48

I suspect one of these packages is to blame for the issue. Probably DKMS or shim-signed, I doubt libssh2 or cpufrequtils have anything to do with it.

How can I investigate further, and ideally, switch back to the Nvidia proprietary driver?

---

### Post by Autodave on 2019-02-20
The 410.93 package is the newest one that *should* work.

A couple thoughts come to mind.  How is the monitor connected?  Have you checked the cable to make sure it is connected tightly?  Have you tried another cable? (Cables do fail.)  Are you using the drivers from the repositories or directly from Nvidia?

---

### Post by user9992 on 2019-02-20
Version 410.93 does not show up in "Additional Drivers" on Ubuntu 14.04.
Available versions are: 384.130 (which is marked as "tested" by Ubuntu), 304.135 ("legacy binary driver") and 340.102.

The monitor is connected via HDMI. I've not tried another cable, but it looks like a software issue to me.

I'm using the drivers from the repository (installed from the "Additional Drivers" tab).

It seems I'm not the only one affected by this problem: [https://askubuntu.com/questions/1119704/ubuntu-works-without-nvidia-but-stuck-at-login-screen-with-nvidia](https://askubuntu.com/questions/1119704/ubuntu-works-without-nvidia-but-stuck-at-login-screen-with-nvidia)

---

### Post by CatKiller on 2019-02-20
The [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) will give you access to later drivers. As Autodave says, the 410 series is the last that will work with that graphics card. It does seem plausible that it's a change to your DKMS configuration that's caused a problem with loading the Nvidia driver. Potentially a newer version of the driver will work better with the current state of the machine.

If you still have trouble logging in with a newer driver, /var/log/Xorg.log and dmesg may help to pin down the problem. Also take note of any messages when installing the drivers: doing so through the terminal will give more output.

It's worth noting that 14.04 will reach End-of-Life in April. It's time to start planning the upgrade.

---

### Post by mc4man on 2019-02-20
On 14.04 here I 'm using the 384 driver from Ubuntu repo. It works fine on  4.4.0-142-generic kernel but not on the 4.4.0-143-generic which was this update - 
> linux-meta-lts-xenial (4.4.0.143.124) trusty; urgency=medium

  * signing: only install a signed kernel (LP: #1764794)
    - switch to signed-only binary packages
    - convert linux-signed* into transitional packages

 -- Kleber Sacilotto de Souza <kleber.souza@canonical.com>  Wed, 13 Feb 2019 15:02:46 +0100

Which kernel are you using?

You could also the ppa as mentioned..

---

### Post by user9992 on 2019-02-21
I can't use the 410 branch, as the GT 630 I've got is based on a Fermi GPU (GF108).

I guess I could use the 390 branch from the PPA, but I'm not sure I want to install drivers from a PPA. It says:
> ## WARNINGS:

 This PPA is currently in testing, you should be experienced with packaging before you dive in here


I think I'll try re-installing nvidia-384 from the command line when I  have time (this is my work PC), and I'll pay attention to any messages  that show up.

I know Ubuntu 14.04 won't be supported any more after April. A fresh install of 18.04 is planned. But thanks for the reminder :wink:

As for the kernel version, I'm on 3.13.0-165-generic. I tried several older versions on Monday, but it didn't help.

---

### Post by CatKiller on 2019-02-21
> **user9992 said:**
> I can't use the 410 branch, as the GT 630 I've got is based on a Fermi GPU (GF108).

```

Version: 	410.93
Supported products

NVIDIA TITAN Series:NVIDIA  TITAN V, NVIDIA TITAN Xp, NVIDIA TITAN X (Pascal), GeForce GTX TITAN X,  GeForce GTX TITAN, GeForce GTX TITAN Black, GeForce GTX TITAN Z

GeForce RTX 20 Series:GeForce RTX 2080 Ti, GeForce RTX 2080, GeForce RTX 2070

GeForce MX100 Series (Notebook):GeForce MX150, GeForce MX130, GeForce MX110

GeForce 10 Series:GeForce  GTX 1080 Ti, GeForce GTX 1080, GeForce GTX 1070 Ti, GeForce GTX 1070,  GeForce GTX 1060, GeForce GTX 1050 Ti, GeForce GTX 1050, GeForce GT 1030

GeForce 10 Series (Notebooks):GeForce GTX 1080, GeForce GTX 1070, GeForce GTX 1060, GeForce GTX 1050 Ti, GeForce GTX 1050

GeForce 900 Series:GeForce GTX 980 Ti, GeForce GTX 980, GeForce GTX 970, GeForce GTX 960, GeForce GTX 950

GeForce 900M Series (Notebooks):GeForce  GTX 980, GeForce GTX 980M, GeForce GTX 970M, GeForce GTX 965M, GeForce  GTX 960M, GeForce GTX 950M, GeForce 945M, GeForce 940MX, GeForce 930MX,  GeForce 920MX, GeForce 940M, GeForce 930M, GeForce 920M, GeForce 910M

GeForce 800M Series (Notebooks):GeForce  GTX 880M, GeForce GTX 870M, GeForce GTX 860M, GeForce GTX 850M, GeForce  845M, GeForce 840M, GeForce 830M, GeForce 825M, GeForce 820M, GeForce  810M

GeForce 700 Series:GeForce  GTX 780 Ti, GeForce GTX 780, GeForce GTX 770, GeForce GTX 760, GeForce  GTX 760 Ti (OEM), GeForce GTX 750 Ti, GeForce GTX 750, GeForce GTX 745,  GeForce GT 740, GeForce GT 730, GeForce GT 720, GeForce GT 710

GeForce 700M Series (Notebooks):GeForce  GTX 780M, GeForce GTX 770M, GeForce GTX 765M, GeForce GTX 760M, GeForce  GT 755M, GeForce GT 750M, GeForce GT 745M, GeForce GT 740M, GeForce GT  735M, GeForce GT 730M, GeForce GT 720M, GeForce 710M

GeForce 600 Series:GeForce  GTX 690, GeForce GTX 680, GeForce GTX 670, GeForce GTX 660 Ti, GeForce  GTX 660, GeForce GTX 650 Ti BOOST, GeForce GTX 650 Ti, GeForce GTX 650,  GeForce GTX 645, GeForce GT 640, GeForce GT 635, GeForce GT 630

GeForce 600M Series (Notebooks):GeForce  GTX 680MX, GeForce GTX 680M, GeForce GTX 675MX, GeForce GTX 670MX,  GeForce GTX 660M, GeForce GT 650M, GeForce GT 645M, GeForce GT 640M,  GeForce GT 640M LE

Quadro RTX Series:Quadro RTX 8000, Quadro RTX 6000, Quadro RTX 5000, Quadro RTX 4000

Quadro Series:Quadro  GV100, Quadro GP100, Quadro P6000, Quadro P5200, Quadro P5000, Quadro  P4000, Quadro P2000, Quadro P1000, Quadro P620, Quadro P600, Quadro  P400, Quadro M6000 24GB, Quadro M6000, Quadro M5000, Quadro M4000,  Quadro M2000, Quadro K6000, Quadro K5200, Quadro K5000, Quadro K4000,  Quadro K4200, Quadro K2200, Quadro K2000, Quadro K2000D, Quadro K1200,  Quadro K620, Quadro K600, Quadro K420, Quadro 410

Quadro Series (Notebooks):Quadro  P5200, Quadro P5000, Quadro P4200, Quadro P4000, Quadro P3200, Quadro  P3000, Quadro P2000, Quadro P1000, Quadro P600, Quadro P500, Quadro  M2200, Quadro M1200, Quadro M620, Quadro M520, Quadro M5500, Quadro  M5000M, Quadro M4000M, Quadro M3000M, Quadro M2000M, Quadro M1000M,  Quadro M600M, Quadro M500M, Quadro K5100M, Quadro K5000M, Quadro K4100M,  Quadro K4000M, Quadro K3100M, Quadro K2200M, Quadro K2100M, Quadro  K3000M, Quadro K2000M, Quadro K1100M, Quadro K1000M, Quadro K620M,  Quadro K610M, Quadro K510M, Quadro K500M

Quadro Blade/Embedded Series :Quadro P5000, Quadro P3000, Quadro M5000 SE, Quadro M3000 SE, Quadro K3100M

Quadro NVS Series:NVS 810, NVS 510

Quadro Sync Series:Quadro Sync II, Quadro Sync, Quadro G-Sync II

Quadro SDI:Quadro SDI

GRID Series:GRID K520

NVS Series:NVS 810, NVS 510

M-Class:M40 24GB, M40

```

> I guess I could use the 390 branch from the PPA, but I'm not sure I want to install drivers from a PPA. It says:




The warning is about joining the team, not about just using the PPA.

Whether you use the PPA or not, consulting the log files may help identify the issue you're having.

---

### Post by oldrocker99 on 2019-02-21
You absolutely need to install 18.04. The poster above is right; support will cease April '19.

---

### Post by mc4man on 2019-02-21
> **user9992 said:**
> I can't use the 410 branch, as the GT 630 I've got is based on a Fermi GPU (GF108).

I guess I could use the 390 branch from the PPA, but I'm not sure I want to install drivers from a PPA. It says:


I think I'll try re-installing nvidia-384 from the command line when I  have time (this is my work PC), and I'll pay attention to any messages  that show up.

I know Ubuntu 14.04 won't be supported any more after April. A fresh install of 18.04 is planned. But thanks for the reminder :wink:

As for the kernel version, I'm on 3.13.0-165-generic. I tried several older versions on Monday, but it didn't help.
I'd suggest installing from a terminal, read thru the output.. see if anything interesting is printed. 

(- here I can't get any nvidia driver installed if booting to the 3.13.x kernel, it says skipping module build as no kernel source, even though I believe the source is installed..  

I'm using the lts-xenial kernel normally, that works fine thru 4.4.0.142.xx, the break comes with the 143 which is in proposed and can stay there.. This also affects 16.04 on the release kernel (4.4.0.143) which is also currently in proposed.
[https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-xenial/+bug/1816768](https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-xenial/+bug/1816768)

---

### Post by user9992 on 2019-02-22
To clarify: there are several versions of the GT 630. Some are Kepler based, and others use a Fermi GPU: [https://en.wikipedia.org/wiki/GeForce_600_series#GeForce_600_(6xx)_series](https://en.wikipedia.org/wiki/GeForce_600_series#GeForce_600_(6xx)_series)
I've got the Fermi version.

Anyway, I tried installing nvidia-384 from the terminal (**sudo apt-get install nvidia-384**), and didn't notice any errors (I saved the output to a file in case I need it later).

The part about DKMS said:
> 
Loading new nvidia-384-384.130 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-165-generic
Building for architecture x86_64
Building initial module for 3.13.0-165-generic
Secure Boot not enabled on this system.
Done.

nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-165-generic/updates/dkms/

nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-165-generic/updates/dkms/

nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-165-generic/updates/dkms/

nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-165-generic/updates/dkms/

depmod....

DKMS: install completed.


However after a reboot, I was back to 1024x768 and couldn't login.

I've copied /var/log/Xorg.0.log to my homedir from the terminal, and noticed the following errors:
> 
[    20.576] (EE) NVIDIA: Failed to initialize the NVIDIA kernel module. Please see the
[    20.576] (EE) NVIDIA:     system's kernel log for additional error messages and
[    20.576] (EE) NVIDIA:     consult the NVIDIA README for details.
[    20.576] (EE) [drm] KMS not enabled
[    20.576] (EE) open /dev/dri/card0: No such file or directory
[    20.576] (WW) Falling back to old probe method for modesetting
[    20.576] (EE) open /dev/dri/card0: No such file or directory
...
[    20.576] (WW) Falling back to old probe method for vesa
[    20.576] (EE) Screen 0 deleted because of no matching config section.
...
[    20.577] (EE) FBDEV(0): FBIOBLANK: Invalid argument
...
[    20.584] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
...
[    20.606] (EE) FBDEV(0): FBIOBLANK: Invalid argument


I've also copied /var/log/kern.log just in case (not sure it's useful). I searched for "nvidia" and "nv" but didn't see any errors.

---

### Post by CatKiller on 2019-02-22
Do you have anything in your grub configuration that would interfere with the loading of the nvidia kernel module? Particular suspects would be things that invoke a framebuffer.

---

### Post by Autodave on 2019-02-22
Is it possible that the 14.04 won't support the newer Nvidia drivers?

---

### Post by mc4man on 2019-02-22
Are you using secure boot? (if not why do you have shim-signed installed?
Out of curiosity what version of xserver do you have,  inxi -G  will show.

(- I'd suspect that if you install the lts-xenial kernel & xserver things may work (not from -proposed..

---

### Post by user9992 on 2019-02-25
Here's the content of /etc/default/grub:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
I don't see anything that would interfere with the Nvidia drivers


Secure Boot should be off. When installing nvidia-384 from the terminal, it clearly said:
> Secure Boot not enabled on this system.
But I think it was enabled when Ubuntu was initially installed.
Ubuntu asked to disable it at one point. Either when installing the Nvidia drivers, or after an update (it was years ago, I don't remember fully).
It required to set a password and to reboot.

Here's the output of "inxi -G":
```

Graphics:  Card: NVIDIA GF108 [GeForce GT 630] 
           X.Org: 1.15.1 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on NVC1 GLX Version: 3.0 Mesa 10.1.3

```

---

### Post by user9992 on 2019-02-27
Another user on [Ask Ubuntu]("https://askubuntu.com/a/1121510") solved it by uninstalling shim-signed. It should be worth a try.

Interestingly, here's the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04.10/changelog") for the DKMS package from [trusty-updates]("https://packages.ubuntu.com/trusty-updates/dkms"):
```

dkms (2.2.0.3-1.1ubuntu5.14.04.10) trusty; urgency=medium

  * debian/patches/shim_secureboot_support.patch:
    - Move to signing just after module build to ensure it correctly applies
      at kernel update times. (LP: #1772950)
    - Generate a new MOK if there isn't one yet, and use that so sign
      newly-built kernel modules. (LP: #1748983)
  * debian/control: Breaks: shim-signed (<< 1.33.1~14.04.4) to ensure both
    are updated in lock-step since the changes above require a new version of
    update-secureboot-policy to correctly generate the new MOK and enroll it
    in firmware.

 -- Mathieu Trudel-Lapierre <cyphermox@ubuntu.com>  Mon, 28 Jan 2019 11:05:49 -0500

```

---

### Post by mikel-losada on 2019-02-27
Hello, I just solved a similar issue on Ubuntu 18.04. It's an issue that I had in the past with Ubuntu 16.04 too and Arch Linux. I was blacklisting the modules that are suggested at several forums but Nouveau would still load on startup, and when I got the Nvidia driver to load the screen was black or with a low resolution.

First of all I removed and purged the nvidia drivers and reinstalled them (nvidia-driver-415).

Let's check which modules are related to Nouveau in the system:

```
$ lsmod | grep nouveau

nouveau              1716224  0
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
video                  45056  2 i915,nouveau
i2c_algo_bit           16384  2 i915,nouveau
ttm                   106496  1 nouveau
drm_kms_helper        172032  3 nvidia_drm,i915,nouveau
drm                   401408  12 drm_kms_helper,nvidia_drm,i915,ttm,nouveau

```

As I said, at /etc/modprobe.d/blacklist.conf I was blacklisting several modules:

```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

```

It turns out that this blacklist is incomplete for my system. As you can see in the output of lsmod above, the modules mxm_wmi and ttm are related and exclusive to Nouveau in my system. So I blacklisted those two at blacklist.conf too:

```

blacklist ttm
blacklist mxm_wmi

```

Remember to run update-initramfs -u after you make these changes so the kernel blacklists these modules.

I also edited /etc/default/grub and made this change:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" 
```

```

sudo update-grub
sudo reboot

```

To make sure that my nvidia-415 driver is properly loaded, I run a tiny OpenGL program that outputs the current version (the Nouveau driver will restrict you to an ancient 3.x version):

```

Renderer: GeForce GTX 1050 Ti/PCIe/SSE2
OpenGL version supported 4.6.0 NVIDIA 415.27

```

As you can see it's now loading successfully. My low resolution and black screen issues are gone too.

---

### Post by user9992 on 2019-02-27
OK, that worked:
```

sudo apt-get remove shim-signed
sudo apt-get install nvidia-384

```
And then reboot.

Reminder (to anyone who reads this in the future):
Make sure Secure Boot is disabled before uninstalling shim-signed.

---

### Post by mc4man on 2019-02-27
> **user9992 said:**
> OK, that worked:
```

sudo apt-get remove shim-signed
sudo apt-get install nvidia-384

```
And then reboot.

Reminder (to anyone who reads this in the future):
Make sure Secure Boot is disabled before uninstalling shim-signed.

You should be good now..
Users of nvidia with 14.04 on the xenial-lts and 16.04 release kernel itself should be wary of kernel updates from proposed as same issue will occur
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1573508](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1573508)

---

### Post by gonzo66 on 2019-03-21
Dear mc4man,

I have exactly the same case as yours. I have installed Nvidia driver 410.48, and stop working when kernel was updated to .143 .
I do not see a secure boot option in the BIOS menu, but if I do

>> ls -l /sys/firmware/efi/efivars/Secure*
-rw-r--r-- 1 root root 5 Mar 21 18:03 /sys/firmware/efi/efivars/SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c

so, I am not sure if secure boot is enabled or not... Should still do
sudo apt-get remove shim-signed

?



I still can pick the previous kernel from GRUB,and works perfectly..... so I do not want to mess with the NVIDIA drivers..., It does not seem wise to do

sudo apt-get install nvidia-384if the drivers works with all the other kernels from GRUB..
Please give me some advice.


Thank you


> **mc4man said:**
> You should be good now..
Users of nvidia with 14.04 on the xenial-lts and 16.04 release kernel itself should be wary of kernel updates from proposed as same issue will occur
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1573508](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1573508)

---

### Post by mc4man on 2019-03-21
> **gonzo66 said:**
> Dear mc4man,

I have exactly the same case as yours. I have installed Nvidia driver 410.48, and stop working when kernel was updated to .143 .
I do not see a secure boot option in the BIOS menu, but if I do

>> ls -l /sys/firmware/efi/efivars/Secure*
-rw-r--r-- 1 root root 5 Mar 21 18:03 /sys/firmware/efi/efivars/SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c

so, I am not sure if secure boot is enabled or not... Should still do
sudo apt-get remove shim-signed

?



I still can pick the previous kernel from GRUB,and works perfectly..... so I do not want to mess with the NVIDIA drivers..., It does not seem wise to do

sudo apt-get install nvidia-384if the drivers works with all the other kernels from GRUB..
Please give me some advice.


Thank you
Ubuntu fixed nvidia driver packages for this but only the ones they support. The graphics driver ppa apparently hasn't yet. Whether they ever do so for 14.04 I've no clue

I'd go with newer drivers & use the 142 kernel (unless ppa takes care of this..

---

### Post by nerv-agent on 2019-03-21
I'm having a similar problem:

[https://ubuntuforums.org/showthread.php?t=2415098](https://ubuntuforums.org/showthread.php?t=2415098)

So this means I have to wait for some devs to release a new driver?

---

### Post by wildmanne39 on 2019-03-21
Hello nerv-agent please do not post for help in someone else's thread, continue in your own.

Thanks!

---

### Post by halljam on 2020-02-18
> **mc4man said:**
> You should be good now..
Users of nvidia with 14.04 on the xenial-lts and 16.04 release kernel itself should be wary of kernel updates from proposed as same issue will occur
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1573508](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-361/+bug/1573508)

I want to thank you guys. I had so many problems with the update breaking my Nvidia drivers which stuck me on 800x600 on my htpc. I tried so many things I found on Google related to the drivers, but I never imagined that it would be related to this shim-signed package or driver signing. The hint to remove that helped out a lot and all of a sudden I could do 1920x1080 again. Thank you.

---

### Post by ishtiaqueayon on 2020-05-23
I'm currently on 20.04 and successfully installed 920m driver. But sometimes my screen freezes and it lasts for 3-4 seconds. I've also felt some kind of frame loss during scrolling on the browser.

---

### Post by coffeecat on 2020-05-23
Old solved thread closed to prevent further necro-hijacks.

@ishtiaqueayon, please start your own thread.

---

