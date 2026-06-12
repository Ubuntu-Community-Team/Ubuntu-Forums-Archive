---
title: "Ubuntu Gnome 16.04 LTS | Flashing text on boot with proprietary nvidia-340 driver."
date: 2018-01-22
forum: General Help
---

### Post by quenz on 2018-01-22
MacBook Pro (13-inch, Mid 2009)
Model #: A1278
GPU: NVIDIA GeForce 9400M (256MB)

The open-source driver works fine, but it is slow. I ran tests from [GpuTest]("http://www.geeks3d.com/gputest/") on both Mac OS and Ubuntu Gnome (with the open source driver), as well as some tests from [browserbench.org]("http://browserbench.org/") with the latest version of Firefox in each OS. Ubuntu is consistently slower than Mac OS. So I want to try the proprietary Nvidia driver, to see if it's any faster.

I get a flashing log of text when I try to boot after selecting the nvidia-340 driver, with some green [ OK ]'s or something like that. I can get into shell with Ctrl+Alt+F1 sometimes, but sometimes it's difficult, or impossible.

Here are some logs I gave to someone trying to help me on IRC, they said I should show them to others trying to help to avoid them reinventing the wheel: [http://termbin.com/g584](http://termbin.com/g584) [http://termbin.com/yjab](http://termbin.com/yjab)

---

### Post by Bashing-om on 2018-01-22
quenz; Hey ;

As I am somewhat familiar with your issue - I will pick it back up here .

Post back the outputs of terminal commands:
```

lsb_release -a
uname -r
dpkg -l | grep linux-
dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```

with the thought in mind to revert the kernel to xenial's default ( OR fresh install 16.04.[color=red]1[/color]

[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

### Post by quenz on 2018-01-22
```

quenz@quenz-MacBookPro:~$ lsb release -a
No command 'lsb' found, did you mean:
 Command 'jsb' from package 'jsonbot' (universe)
 Command 'msb' from package 'mysql-sandbox' (universe)
 Command 'lsw' from package 'suckless-tools' (universe)
 Command 'sb' from package 'lrzsz' (universe)
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'lb' from package 'live-build' (main)
 Command 'lsx' from package 'suckless-tools' (universe)
 Command 'ls' from package 'coreutils' (main)
lsb: command not found
quenz@quenz-MacBookPro:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

```

quenz@quenz-MacBookPro:~$ uname -r
4.13.0-31-generic

```

```

quenz@quenz-MacBookPro:~$ dpkg -l |grep linux-
ii  linux-base                                  4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                              1.157.11                                     all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-16.04                     4.13.0.31.51                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.10.0-28                     4.10.0-28.32~16.04.2                         all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-28-generic             4.10.0-28.32~16.04.2                         amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-31                     4.13.0-31.34~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-31-generic             4.13.0-31.34~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04             4.13.0.31.51                                 amd64        Generic Linux kernel headers
ii  linux-image-4.10.0-28-generic               4.10.0-28.32~16.04.2                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-31-generic               4.13.0-31.34~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic         4.10.0-28.32~16.04.2                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-31-generic         4.13.0-31.34~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04               4.13.0.31.51                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-87.110                                 amd64        Linux Kernel Headers for development
ii  linux-signed-generic-hwe-16.04              4.13.0.31.51                                 amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.13.0-31-generic        4.13.0-31.34~16.04.1                         amd64        Signed kernel image generic
ii  linux-signed-image-generic-hwe-16.04        4.13.0.31.51                                 amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

Nothing happened here:
```
quenz@quenz-MacBookPro:~$ dpkg -l | grep -i nvidia
```

```

quenz@quenz-MacBookPro:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.13.0-31-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.13.0-31-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is fglrx kernel module available? no
Is nvidia kernel module available? no
Vendor/Device Id: 10de:863
BusID "PCI:2@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "nouveau"
Found "/dev/dri/card0", driven by "nouveau"
output 0:
    card0-LVDS-1
Number of connected outputs for /dev/dri/card0: 1
Skipping "/dev/dri/card0", driven by "nouveau"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? no
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? no
Is prime egl available? no
Single card detected
Kernel Module is not loaded
Nothing to do
No change - nothing to do

```

---

### Post by quenz on 2018-01-22
I've reinstalled again (before typing the above commands). I tried to enable the proprietary Broadcom wireless driver, because the open-source one doesn't work any good, but when I select it, then click apply, it just reverts back to "Do not use this device".

---

### Post by Bashing-om on 2018-01-22
quenz; well.

The only issue I see is that old EOL kernel - 4.10.0-28 that presently we can not do a thing about.

Have you tried building the nvidia driver on this new 4.13.0-31 kernel ? Maybe the -25/26 kernel issues with nvidia are now resolved :)
Or - see what we can do on the xenial 4.4.0-109-generic kernel ??


As to broadcom:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://ubuntuforums.org/showthread.php?t=2343228](https://ubuntuforums.org/showthread.php?t=2343228)

[INDENT][INDENT]sometimes I do wonder[/INDENT][/INDENT]

---

### Post by quenz on 2018-01-23
> **Bashing-om said:**
> The only issue I see is that old EOL kernel - 4.10.0-28 that presently we can not do a thing about.

But as you can see in [COLOR=#000000][FONT=&amp]uname -r[/FONT][/COLOR], I'm on [COLOR=#000000][FONT=&amp]4.13.0-31-generic[/FONT][/COLOR], and like I said I'm on a fresh install, so I've never used 4.10 on this one.
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]> **Bashing-om said:**
> Have you tried building the nvidia driver on this new 4.13.0-31 kernel ? Maybe the -25/26 kernel issues with nvidia are now resolved :)

By building, do you just mean installing? I'm not sure what the -25/26 issues are.

I don't actually remember if I tried to enable nvidia-340 on this fresh install yet, I'll check soon.


> **Bashing-om said:**
> 
As to broadcom:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://ubuntuforums.org/showthread.php?t=2343228](https://ubuntuforums.org/showthread.php?t=2343228)[INDENT][INDENT]sometimes I do wonder[/INDENT]
[/INDENT]


I guess I can try from terminal, but I did it fine in the Additional Drivers GUI last install.

---

### Post by quenz on 2018-01-23
> **Bashing-om said:**
> Or - see what we can do on the xenial 4.4.0-109-generic kernel ??

I don't quite follow.

---

### Post by Bashing-om on 2018-01-23
quenz; K;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302) ( Kernel 4.13.0-25 broke nvidia driver)
One of several reports .
In your case we can not go to a later generation graphic's driver. The recommended driver for your card is the 340 version.
As this is older hardware, an older kernel ( 16.04.1 ) may be the more suitable  ?

As to BCM no direct experience, so can not comment further.

[INDENT][INDENT]but a know it all, I am not[/INDENT][/INDENT]

---

### Post by quenz on 2018-01-23
> **Bashing-om said:**
> 
As this is older hardware, an older kernel ( 16.04.1 ) may be the more suitable  ?

In grub, I have a choice between Linux 4.13.0-31-generic and 4.10.0-28-generic. I'm not sure what 16.04.1 is referring to. If it's a kernel, I don't have that option currently.

---

### Post by Bashing-om on 2018-01-23
quenz; Hey -

Sorry that I was unclear .. the specific point release of 16.04 the .1 incorporates the 4.4 series kernels .
As of last update the version for xenial proper is :
> 
sysop@x1604:~$ uname -r
4.4.0-112-generic
sysop@x1604:~$


As the 4.10 kernel is from the zesty release, and zesty is no longer in support - there is no support for that kernel -  we do not want to do anything with that version . As you only have these 2 kernels installed there is but the one option here : See if you can install the proprietary nvidia graphic's driver on the 4.13.0-31 version:
```

sudo apt update
sudo apt full-upgrade

```

Reboot the system as we may pick up new versions of installed packages ( think a new kernel !) .

Now let's install the proprietary driver:
```
 
sudo ubuntu-drivers autoinstall

```
which will install the 340 version driver .

Reboot and let's see the effect ..

Still failing I am all for a fresh new install of the 16.04.1 NOT 16.04.3 . The .3 has the HardWare Enablement (HWE) stack with the 17.10 kernel ( 3.13.XXX) . I do feel that older hardware has the better compatibility with the 4.4 kernel . And you have the less overhead and maintenance with the 4.4 series kernel .
See: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[INDENT][INDENT]one way does not work
[INDENT][INDENT][INDENT]try another[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by quenz on 2018-01-23
It works! I followed the commands you posted above. And it definitely seems a lot faster than it did with the open-source driver.

The only issue I see is: when I click the activities menu thingy in the corner, a glitchy green bar appears and disappears depending on where I move my mouse.

---

### Post by Bashing-om on 2018-01-23
quenz; Great !

That on the 4.13.0-31 kernel ?

As to the " glitchy green bar appears" I have no idea of what we can do for that ,

just goes to show
[INDENT][INDENT]what some effort can do
[/INDENT][/INDENT]

---

### Post by quenz on 2018-01-23
> **Bashing-om said:**
> That on the 4.13.0-31 kernel ?

Correct!

> **Bashing-om said:**
> 
As to the " glitchy green bar appears" I have no idea of what we can do for that


Perhaps I should start a new thread for this new issue?

Also, just to confirm, from a fresh install, I should be able to type these commands:

```

sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
reboot

```

And everything should be good? I want to be able to know how to make everything work start-to-finish, in case I ever need to reinstall for whatever reason.

---

### Post by Bashing-om on 2018-01-23
quenz; Outstanding :)

Glad to know the -31 kernel works /

As to the installation of the driver on a new fresh install:
```

sudo apt update
sudo apt full-upgrade

```
reboot as new packages will be installed -
now one can run:
```

sudo ubuntu-drivers autoinstall

```

and re-boot again to see the effect.

If this matter is concluded to your satisfaction :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And yes start a new thread on the green glitch .

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by quenz on 2018-01-24
I've reinstalled the OS. I wanted to see if I could just run all the commands, then just reboot once, which I did, and it worked fine.

---

