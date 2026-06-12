---
title: "No Splash Screen During Boot?"
date: 2016-07-20
forum: General Help
---

### Post by sasafrass452 on 2016-07-20
I noticed that I don't see the splash screen during boot up. It was there before. Was something changed with an update? I do see a blank purple screen, but no logo. Is there a setting for this?

It seems that this is an intermittent issue. Not sure why it's happening. Any thoughts or suggestions?

---

### Post by yoshii on 2016-08-02
There is a setting to turn this off or on, manually, but if you didn't initiate it (by deleting text in /etc/default/grub) then it is some kind of bug or design flaw or conflict.  
It sounds like some kind of a graphics driver issue.  If you recently upgraded to v16.04 or similar, it is a common issue that especially affects ATI / AMD / Radeon graphics hardware.  

Personally, I like to disable the splash screen so that I can instead see the commands as they are run.  But if you see no text during boot, then you're probably still in splash mode but something is wrong.  

But what you can do is... 

invoke your text editor (but not using LibreOffice nor AbiWord... use gedit or mousepad or leafpad or geany) and edit /etc/default/grub
You will need to use "sudo" as a prefix for permission and safety reasons, since it's a very important and delicate file.  

If you don't use sudo, you don't have to worry about messing it up because changes won't be saved (unless you are already in root mode).  

Anyways.

It will look something a little bit like this:

```

# If you change this file, run 'sudo update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT="saved"
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT="true"
# GRUB_HIDDEN_TIMEOUT=0
# GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="rootfstype=ext4"
GRUB_CMDLINE_LINUX=""

```

The line of interest is the line that is "GRUB_CMDLINE_LINUX_DEFAULT=" etcetera.  
If you delete what's between the quotes on your ssytem (if it says something about "splash" and "quiet") then it will boot with the text boot messages visible under normal circumstances.  

But since yours isn't working, you may want to enter "nomodeset" there instead.  
That kernel boot parameter has something to do with disabling hardware acceleration of the graphics card and using some kind of lesser, more compatible mode instead, I believe.  

If you've had to enter other parameters, leave those there between the quotes as well.  I think they are separated by commas.  I'm not 100% sure, so you will want to check other sources.  

Mine has "rootfstype=ext4" because I recently converted my filesystem to ext4 from ext3.  This tells the kernel to mount and use ext4 as the filesystem in case it can't otherwise be read i guess or something like that.  

Anyways, try using ="nomodeset" on that line, and then when you are done editing, save and then from the command line, run "sudo update-grub".  
That last step is mandatory and must not be interrupted because it's re-writing the boot loader with the new info.  

But even if nomodeset doesn't work, the procedure is similar for other "kernel boot commands" or kernel boot options or kernel boot parameters or whatever a person wants to call them.  Others will know more about this.  And there are on the internet lists of these kernel boot option parameters/commands available to fix certain hardware issues that may or may not affect different models of computers.  

It's worth it in your reply to tell us what type of computer you have as well as the graphics card and which version of ubuntu you are using.  
The people who know more than me here, and there are lots, will have a better idea then how to help you.  

Good luck.

---

### Post by sasafrass452 on 2016-08-03
Thankyou for your response. I didn't *purposely* change anything that would've effected this. I'm not sure if I did anything to change it or not.... that is to say I didn't edit the file you're pointing me to, or any other file. I recently got a new laptop, a Lenovo G50 with an AMD processor & radeon graphics. However, my mother also just got the same laptop, yet the splash screen appears during bootup. We are both using Ubuntu 16.04, fully updated. Here is what my grub file says.... What should I do?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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

> **yoshii said:**
> There is a setting to turn this off or on, manually, but if you didn't initiate it (by deleting text in /etc/default/grub) then it is some kind of bug or design flaw or conflict.  
It sounds like some kind of a graphics driver issue.  If you recently upgraded to v16.04 or similar, it is a common issue that especially affects ATI / AMD / Radeon graphics hardware.  

Personally, I like to disable the splash screen so that I can instead see the commands as they are run.  But if you see no text during boot, then you're probably still in splash mode but something is wrong.  

But what you can do is... 

invoke your text editor (but not using LibreOffice nor AbiWord... use gedit or mousepad or leafpad or geany) and edit /etc/default/grub
You will need to use "sudo" as a prefix for permission and safety reasons, since it's a very important and delicate file.  

If you don't use sudo, you don't have to worry about messing it up because changes won't be saved (unless you are already in root mode).  

Anyways.

It will look something a little bit like this:

```

# If you change this file, run 'sudo update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT="saved"
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT="true"
# GRUB_HIDDEN_TIMEOUT=0
# GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="rootfstype=ext4"
GRUB_CMDLINE_LINUX=""

```

The line of interest is the line that is "GRUB_CMDLINE_LINUX_DEFAULT=" etcetera.  
If you delete what's between the quotes on your ssytem (if it says something about "splash" and "quiet") then it will boot with the text boot messages visible under normal circumstances.  

But since yours isn't working, you may want to enter "nomodeset" there instead.  
That kernel boot parameter has something to do with disabling hardware acceleration of the graphics card and using some kind of lesser, more compatible mode instead, I believe.  

If you've had to enter other parameters, leave those there between the quotes as well.  I think they are separated by commas.  I'm not 100% sure, so you will want to check other sources.  

Mine has "rootfstype=ext4" because I recently converted my filesystem to ext4 from ext3.  This tells the kernel to mount and use ext4 as the filesystem in case it can't otherwise be read i guess or something like that.  

Anyways, try using ="nomodeset" on that line, and then when you are done editing, save and then from the command line, run "sudo update-grub".  
That last step is mandatory and must not be interrupted because it's re-writing the boot loader with the new info.  

But even if nomodeset doesn't work, the procedure is similar for other "kernel boot commands" or kernel boot options or kernel boot parameters or whatever a person wants to call them.  Others will know more about this.  And there are on the internet lists of these kernel boot option parameters/commands available to fix certain hardware issues that may or may not affect different models of computers.  

It's worth it in your reply to tell us what type of computer you have as well as the graphics card and which version of ubuntu you are using.  
The people who know more than me here, and there are lots, will have a better idea then how to help you.  

Good luck.

Here is more specific info on my processor & graphics:

AMD A8-6410 APU with AMD Radeon R5 Graphics × 4
Gallium 0.4 on AMD MULLINS (DRM 2.43.0, LLVM 3.8.0)

BTW, I do see the splash screen during shutdown, so I can't imagine why it doesn't appear during bootup.

Here is the contents of plymouth-start.service. Looks like the splash screen should be showing, but clearly, something got broken somewhere. I just need to know what went wrong....

```
[Unit]
Description=Show Plymouth Boot Screen
DefaultDependencies=no
Wants=systemd-ask-password-plymouth.path
After=systemd-udev-trigger.service systemd-udevd.service keyboard-setup.service
Before=systemd-ask-password-plymouth.service
ConditionKernelCommandLine=!plymouth.enable=0
ConditionKernelCommandLine=!nosplash
ConditionKernelCommandLine=splash

[Service]
ExecStart=/sbin/plymouthd --mode=boot --pid-file=/run/plymouth/pid --attach-to-session
ExecStartPost=-/bin/plymouth show-splash
Type=forking
KillMode=none
SendSIGKILL=no
```

Ok, I found a solution, though I don't consider it "perfect". Here's what I did:
[https://www.thefanclub.co.za/how-to/how-fix-ubuntu-boot-splash-screen-after-grub-updates](https://www.thefanclub.co.za/how-to/how-fix-ubuntu-boot-splash-screen-after-grub-updates)

---

### Post by gdesilva on 2016-08-10
Have you got the proprietary fglrx driver installed for your AMD card? If not, I would try that first.

---

### Post by sasafrass452 on 2016-08-13
What packages(other than grub) would effect this? If so, what packages should I look for? I've been wondering if I did something to cause this, since the splash screen did appear when I first installed Ubuntu 16.04. I thought perhaps one of the updates caused it? When I search grub in synaptic, here are the packages that are installed:

grub-common
grub-efi-amd64
grub-efi-amd64-bin
grub-efi-amd64-signed
grub2-common

Is anything missing? Should something be removed or reinstalled? Any help is appreciated!

---

### Post by jeebustrain on 2016-09-17
I lose mine whenever I use the proprietary graphics driver (nvidia in my case)

---

### Post by sasafrass452 on 2016-09-18
Ok, I'm really confused.... Should I, or should I not use the proprietary driver? Here's what I currently have installed:

fglrx-pxpress
ubuntu-drivers-common
i965-va-driver
mesa-vdpau-drivers
va-driver-all
vdpau-driver-all
vdpau-va-driver
xserver-xorg-video-all
xserver-xorg-video-amdgpu
xserver-xorg-video-ati
xserver-xorg-video-fbdev
xserver-xorg-video-nouveau
xserver-xorg-video-qxl
xserver-xorg-video-radeon
xserver-xorg-video-radeon-dbg
xserver-xorg-video-vesa
xserver-xorg-video-vmware

So, now what should I do? Any help is appreciated!

---

### Post by Bashing-om on 2016-09-27
sasafrass452; Hey ...

It all depends - on a proprietary driver install for ATI cards - on what release you are running.
Be aware that AMD (ATI cards ) has thrown full support to open source, and there is no proprietary (FGLRX) driver after release 14.04.2 [fully updated system].
The appropriate driver is provided in the kernel in these later releases .

Show us what there is to work with; post back:
```

uname -a
lsb_release -a
lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep fglrx*
lsmod | grep fglrx

```

And we see where we go from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-09-27
I'm running 16.04 on a laptop with an AMD processor, & Radeon R4/5 Mullins graphics driver. Here's what I currently have installed for graphics:

fglrx-pxpress
ubuntu-drivers-common
i965-va-driver
mesa-vdpau-drivers
va-driver-all
vdpau-driver-all
vdpau-va-driver
xserver-xorg-video-all
xserver-xorg-video-amdgpu
xserver-xorg-video-ati
xserver-xorg-video-fbdev
xserver-xorg-video-nouveau
xserver-xorg-video-qxl
xserver-xorg-video-radeon
xserver-xorg-video-radeon-dbg
xserver-xorg-video-vesa
xserver-xorg-video-vmware

> **Bashing-om said:**
> sasafrass452; Hey ...

It all depends - on a proprietary driver install for ATI cards - on what release you are running.
Be aware that AMD (ATI cards ) has thrown full support to open source, and there is no proprietary (FGLRX) driver after release 14.04.2 [fully updated system].
The appropriate driver is provided in the kernel in these later releases .

Show us what there is to work with; post back:
```

uname -a
lsb_release -a
lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep fglrx*
lsmod | grep fglrx

```

And we see where we go from here.[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-27
sasafrass452; Weeelllll..
this:
> 
i965-va-driver

in lieu of the requested lspci command - still indicates this is a hybrid graphics situation.
I am not conversant in 16.04 switching between the Intel/ATI graphic sets . We await others with the experience.

as to the proper driver for a Mullins generation card, we are looking at the open source driver radeon . It is not new enough for the amdgpu (open source also ) driver nor at all for the amdgpu-pro for cutting edge cards .
See: [https://wiki.gentoo.org/wiki/Amdgpu](https://wiki.gentoo.org/wiki/Amdgpu)
as a good reference for what driver matches what card.
So at this point for sure, remove all the FGLRX attempts, and all other conflicting drivers. 
You must run on radeon as it is the only option you have in 16.04 .

I will continue to monitor this thread; offer what little advise I can and  see what works out for you .

[INDENT][INDENT]one of those times
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-09-28
Just to clarify.... I only need [COLOR=#000000]xserver-xorg-video-radeon & [/COLOR][COLOR=#000000]xserver-xorg-video-radeon-dbg, & remove all the others on my list?[/COLOR]

> **Bashing-om said:**
> sasafrass452; Weeelllll..
this:

in lieu of the requested lspci command - still indicates this is a hybrid graphics situation.
I am not conversant in 16.04 switching between the Intel/ATI graphic sets . We await others with the experience.

as to the proper driver for a Mullins generation card, we are looking at the open source driver radeon . It is not new enough for the amdgpu (open source also ) driver nor at all for the amdgpu-pro for cutting edge cards .
See: [https://wiki.gentoo.org/wiki/Amdgpu](https://wiki.gentoo.org/wiki/Amdgpu)
as a good reference for what driver matches what card.
So at this point for sure, remove all the FGLRX attempts, and all other conflicting drivers. 
You must run on radeon as it is the only option you have in 16.04 .

I will continue to monitor this thread; offer what little advise I can and  see what works out for you .[INDENT][INDENT]one of those times[INDENT][INDENT][INDENT]I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-28
sasafrass452; Well,

I have in mind to remove all the ATI driver related files, and install afresh;
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files (sudo apt-get remove --purge fglrx*)
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Maybe overkill . But I do not know what all you have attempted and this "should" take care of removing the old driver files and properly installing the new open source driver.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-09-29
I attempted your suggestion using the codes you posted, & there was no change. I still don't see the splash screen during bootup. However, I did skip xserver-xorg-video-radeon, since I already have it installed. As I stated in my original post, the splash screen did appear when I first installed Ubuntu. But apparently, something changed & it no longer appears during bootup. I don't believe I did anything other than the updates, since I normally don't touch the system files, especially ones that effect the bootup process. Also, I noticed that I still have [COLOR=#000000]xserver-xorg-video-ati & [/COLOR][COLOR=#000000]i965-va-driver[/COLOR][COLOR=#000000] installed. Should I remove them?[/COLOR]

> **Bashing-om said:**
> sasafrass452; Well,

I have in mind to remove all the ATI driver related files, and install afresh;
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files (sudo apt-get remove --purge fglrx*)
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Maybe overkill . But I do not know what all you have attempted and this "should" take care of removing the old driver files and properly installing the new open source driver.
[INDENT][INDENT]just what I think
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-29
sasafrass452; Well;

A couple of thoughts on this;
the presence of i965-va-driver and xserver-xorg-video-radeon indicates that this is a hybrid graphics system;
let's look at what the hardware is:
```

lspci -vnn | grep VGA -A 12
lspci -nnk | grep -i vga -A3 | grep 'in use'
sudo lshw -C display

```
Upfront, with AMD changing the course of their support, I do not know how radeon now handles switching the graphic's sets. This could well be a learning process for all of us .

And as to how splash is called :
in normal situations Plymouth - the splash screen manager- is responsible for reading input. vt.handoff= and having "splash"  on the command-line are needed to make it behave itself .
So, do these parameters exist ?
show:
```

cat /etc/default/grub

```

we will find
[INDENT][INDENT]the path to follow
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-09-29
Here's what terminal says for both codes:

> lspci -vnn | grep VGA -A 12
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 05) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Mullins [Radeon R4/R5 Graphics] [17aa:3801]
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at 3000 [size=256]
    Memory at f0d00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f0a00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]

lspci -nnk | grep -i vga -A3 | grep 'in use'
    Kernel driver in use: radeon

*-display               
       description: VGA compatible controller
       product: Mullins [Radeon R4/R5 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:37 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0d00000-f0d3ffff memory:f0a00000-f0a1ffff

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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





> **Bashing-om said:**
> sasafrass452; Well;

A couple of thoughts on this;
the presence of i965-va-driver and xserver-xorg-video-radeon indicates that this is a hybrid graphics system;
let's look at what the hardware is:
```

lspci -vnn | grep VGA -A 12
lspci -nnk | grep -i vga -A3 | grep 'in use'
sudo lshw -C display

```
Upfront, with AMD changing the course of their support, I do not know how radeon now handles switching the graphic's sets. This could well be a learning process for all of us .

And as to how splash is called :
in normal situations Plymouth - the splash screen manager- is responsible for reading input. vt.handoff= and having "splash"  on the command-line are needed to make it behave itself .
So, do these parameters exist ?
show:
```

cat /etc/default/grub

```

we will find[INDENT][INDENT]the path to follow
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-29
sasafrass452; K;

Well. We roll our sleeves up and go to work .
1) I see no indication of anything other than ATI (Mullins) for graphics . What is an Intel driver doing installed on this system ?

2) Is there not a conflict here in the plymouth-start.service file ?
> 
Before=systemd-ask-password-plymouth.service
ConditionKernelCommandLine=!plymouth.enable=0
ConditionKernelCommandLine=!nosplash
ConditionKernelCommandLine=splash

where I would expect only one " ConditionKernelCommandLine " conditional to be honored .
I be looking to try and find a default file to confirm .

EDIT:
Your file is verified as correct, I am barking up the wrong tree here .
as reference and proof:
My Find:
> 
[Unit]
Description=Show Plymouth Boot Screen
DefaultDependencies=no
Wants=systemd-ask-password-plymouth.path
After=systemd-udev-trigger.service systemd-udevd.service keyboard-setup.service
Before=systemd-ask-password-plymouth.service
ConditionKernelCommandLine=!plymouth.enable=0
ConditionKernelCommandLine=!nosplash
ConditionKernelCommandLine=splash

[Service]
ExecStart=/sbin/plymouthd --mode=boot --pid-file=/run/plymouth/pid --attach-to-session
ExecStartPost=-/bin/plymouth show-splash
Type=forking
KillMode=none
SendSIGKILL=no


3) For continued troubleshooting; is the plymouth-x11 package installed ?
what returns:
```

dpkg -l plymouth-x11

```


EDIT2 :
[https://wiki.ubuntu.com/BootGraphicsArchitecture](https://wiki.ubuntu.com/BootGraphicsArchitecture)
> 
In some cases, the resolution chosen by the kernel may not be the same as that chosen by GRUB; for example, this happens when the BIOS manufacturer has not properly set the native panel resolution as the preferred resolution in VBE. Because of this, we deliberately hand off from GRUB to the kernel with a plain background colour rather than with a logo on the screen, on the grounds that a plain background looks much the same at any resolution. The Ubuntu logo appears on screen once Plymouth starts.

something to keep on mind.

[INDENT][INDENT]homework time
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-09-30
As far as intel goes, I have i965-va-driver & intel-gpu-tools installed. Should I remove them?

I do have plymouth-x11 installed.

> **Bashing-om said:**
> sasafrass452; K;

Well. We roll our sleeves up and go to work .
1) I see no indication of anything other than ATI (Mullins) for graphics . What is an Intel driver doing installed on this system ?

2) Is there not a conflict here in the plymouth-start.service file ?

where I would expect only one " ConditionKernelCommandLine " conditional to be honored .
I be looking to try and find a default file to confirm .

EDIT:
Your file is verified as correct, I am barking up the wrong tree here .
as reference and proof:
My Find:


3) For continued troubleshooting; is the plymouth-x11 package installed ?
what returns:
```

dpkg -l plymouth-x11

```


EDIT2 :
[https://wiki.ubuntu.com/BootGraphicsArchitecture](https://wiki.ubuntu.com/BootGraphicsArchitecture)

something to keep on mind.
[INDENT][INDENT]homework time
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-09-30
sasafrass452; Uh HUh .

If there is no Intel graphic's card on the system, I can see where having the drivers for Intel installed might cause the kernel a bit of consternation.

But there is also this :
is this you too ?
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707)
If so add your voice to aid in squashing this bug .
The report includes a couple of work-a-rounds that might be productive in THAT event 


[INDENT]still
[INDENT][INDENT][INDENT]might be this, could be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-01
I removed those ati related packages, but there was no change. The launchpad posting is not me, but there are some interesting comments. My hope is to find a permanent resolution, rather than one that'll only be changed back with an update. If this is a bug in plymouth, then I can only wait for it to be fixed in a future update.... if that ever happens. It's apparently a very long standing issue, so I'm not holding my breath....

So, what's our next step?

> **Bashing-om said:**
> sasafrass452; Uh HUh .

If there is no Intel graphic's card on the system, I can see where having the drivers for Intel installed might cause the kernel a bit of consternation.

But there is also this :
is this you too ?
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1370707)
If so add your voice to aid in squashing this bug .
The report includes a couple of work-a-rounds that might be productive in THAT event 

[INDENT]still[INDENT][INDENT][INDENT]might be this, could be that
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-10-01
sasafrass452; Hey ...

You got me .. We are in unexplored territory . I do not find a lot of ubuntu documentation for plymouth under systemd.
Let's see, however, what we can learn :
1) What modules are installed ?
show:
```

lsmod

```

2) do we have the plymouth theme available ?
```

ls -al /usr/share/plymouth/themes

```

and can we invoke plymouth from terminal ?
Start another instance of a console interface - ctl+alt+F2
What results :
```

sudo plymouthd
sudo plymouth --show-splash

```

To exit the preview of plymouth - regain the console by executing ctl+alt+F2 again, now terminal command:
```

sudo plymouth --quit

```

Depending on what results is the path we follow, or maybe keep look'n for that path .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-01
Modules:

> drbg                   32768  1ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
rfcomm                 69632  0
bnep                   20480  2
nls_iso8859_1          16384  1
arc4                   16384  2
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
ath10k_pci             45056  0
btusb                  45056  0
ath10k_core           311296  1 ath10k_pci
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
snd_hda_codec_conexant    24576  1
btintel                16384  1 btusb
snd_hda_codec_generic    77824  1 snd_hda_codec_conexant
snd_hda_codec_hdmi     53248  1
ath                    32768  1 ath10k_core
kvm                   540672  0
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel
mac80211              737280  1 ath10k_core
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
dm9601                 16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
irqbypass              16384  1 kvm
snd_hwdep              16384  1 snd_hda_codec
v4l2_common            16384  1 videobuf2_v4l2
cfg80211              565248  3 ath,mac80211,ath10k_core
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
usbnet                 45056  1 dm9601
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
media                  24576  2 uvcvideo,videodev
snd_timer              32768  2 snd_pcm,snd_seq
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  2
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
shpchp                 36864  0
soundcore              16384  1 snd
joydev                 20480  0
edac_mce_amd           24576  0
input_leds             16384  0
serio_raw              16384  0
edac_core              53248  0
fam15h_power           16384  0
i2c_piix4              24576  0
ccp                    36864  0
k10temp                16384  0
ideapad_laptop         24576  0
mac_hid                16384  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  4
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        147456  1 radeon
psmouse               126976  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sdhci_pci              28672  0
sysimgblt              16384  1 drm_kms_helper
sdhci                  45056  1 sdhci_pci
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   364544  48 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
r8169                  81920  0
mii                    16384  3 r8169,dm9601,usbnet
fjes                   28672  0
video                  40960  1 ideapad_laptop

Plymouth is installed:

> drwxr-xr-x 13 root root  4096 Jul 31 09:18 .
drwxr-xr-x  3 root root  4096 Aug  3 08:21 ..
lrwxrwxrwx  1 root root    39 Jul 16 16:27 default.grub -> /etc/alternatives/default.plymouth.grub
lrwxrwxrwx  1 root root    34 Jul 16 16:27 default.plymouth -> /etc/alternatives/default.plymouth
drwxr-xr-x  2 root root  4096 Aug  3 08:21 details
drwxr-xr-x  2 root root  4096 Aug  3 08:21 fade-in
drwxr-xr-x  2 root root 12288 Aug  3 08:21 glow
drwxr-xr-x  2 root root  4096 Aug  3 08:21 script
drwxr-xr-x  2 root root  4096 Aug  3 08:21 solar
drwxr-xr-x  2 root root  4096 Aug  3 08:21 spinfinity
drwxr-xr-x  2 root root 12288 Aug  3 08:21 spinner
drwxr-xr-x  2 root root  4096 Aug  3 08:21 text
lrwxrwxrwx  1 root root    31 Jul 16 16:27 text.plymouth -> /etc/alternatives/text.plymouth
drwxr-xr-x  2 root root  4096 Aug  3 08:21 tribar
drwxr-xr-x  2 root root  4096 Aug  3 08:21 ubuntu-logo
drwxr-xr-x  2 root root  4096 Aug  3 08:21 ubuntu-text

The splash screen did appear when I ran it from terminal. I expected that, since it does appear during shutdown. The big question is, why not during bootup?

---

### Post by Bashing-om on 2016-10-01
sasafrass452; Well ;

What gets called at shutdown is not what is called at bootup ( initramfs ) .
Let's try a shortcut means to get a resolution:
try and change/reset the plymouth theme :
```

sudo update-alternatives --config default.plymouth

```
choose the one you want .. and then make it so:
```

sudo update-initramfs -u

```
Go ahead, and reboot your desktop. You should see a splash screen during system startup .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-02
Still no change.... What should we try next?

> **Bashing-om said:**
> sasafrass452; Well ;

What gets called at shutdown is not what is called at bootup ( initramfs ) .
Let's try a shortcut means to get a resolution:
try and change/reset the plymouth theme :
```

sudo update-alternatives --config default.plymouth

```
choose the one you want .. and then make it so:
```

sudo update-initramfs -u

```
Go ahead, and reboot your desktop. You should see a splash screen during system startup .
[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-10-02
sasafrass452; Humm ...

> 
Still no change.... What should we try next?


Totally surprised. what did actually happen ? Give us some clues ?.. any errors reported ? 
Looks to me like next we set break points in plymouth starting up and see how far it boot gets and where it fails .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-03
Nothing happened at all. No errors, no text, just the same black screen during boot up. Set break points? That sounds a bit, for lack of a better word, dangerous. If my system doesn't boot, then the current installation is toast, & I'll be forced to reinstall Ubuntu & start from scratch. With the upcoming release of 16.10 on the 13th, I can't help but wonder if this issue will be fixed? Since so many packages are changed & removed during an upgrade, I would think this is a possibility. Maybe we should wait for that & see what happens? Or might there be something less drastic than setting break points, that I can try?

> **Bashing-om said:**
> sasafrass452; Humm ...



Totally surprised. what did actually happen ? Give us some clues ?.. any errors reported ? 
Looks to me like next we set break points in plymouth starting up and see how far it boot gets and where it fails .
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-10-03
sasafrass452; well ....

We can take a few more pokes at it :

"Every time a theme is changed, the kernel image must be rebuilt:"
```

sudo plymouth-set-default-theme -R <theme>

```
where <theme> is that last selected theme

And I ran across this: - that does not apply directly to a ubuntu install ! -
> 
On systems that boot quickly, you may only see a flicker of your splash theme before your DM or login prompt is ready. You can set ShowDelay to an interval (in seconds) longer than your boot time to prevent this flicker and [color=red]only show a blank screen[/color]. The default is 5 seconds, but you may wish to change this to a lower value to see your splash earlier during boot.

as the referenced config file does not exist in our world ( /etc/plymouth/plymouthd.conf ) . But ??? maybe elsewhere ??


What I am finding is that the documentation of systemd on ubuntu is not current. I have a 16.04 systemd standard install in a test bed and referenced files do not exist . As I can not duplicate your issue, all we can do is poke and see what we can learn .
Perhaps others with greater experience in 16.04 will respond in this thread to guide us along .

-----------------------
As to installing 16.10 .. well that is an option but bear in mind it is NOT a LTS release. 16.10 will only have 9 months support .

It is all a learning process
[INDENT][INDENT]I am all for what I can learn
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-03
I believe the theme was aleady set as the default, but I tried that code anyway, & terminal says "command not found". As for upgrading to 16.10, I don't mind if it's not the LTS version, since I always upgrade when a new release is available. When I see the prompt to upgrade, I'll do it. Besides, why worry about 9 months of support when I'll be upgrading again in 6 months? Anywho, why won't it be the LTS version? I would think that's what I'll get next week when it's officially out....

So, anything else we can try?

> **Bashing-om said:**
> sasafrass452; well ....

We can take a few more pokes at it :

"Every time a theme is changed, the kernel image must be rebuilt:"
```

sudo plymouth-set-default-theme -R <theme>

```
where <theme> is that last selected theme

And I ran across this: - that does not apply directly to a ubuntu install ! -

as the referenced config file does not exist in our world ( /etc/plymouth/plymouthd.conf ) . But ??? maybe elsewhere ??


What I am finding is that the documentation of systemd on ubuntu is not current. I have a 16.04 systemd standard install in a test bed and referenced files do not exist . As I can not duplicate your issue, all we can do is poke and see what we can learn .
Perhaps others with greater experience in 16.04 will respond in this thread to guide us along .

-----------------------
As to installing 16.10 .. well that is an option but bear in mind it is NOT a LTS release. 16.10 will only have 9 months support .

It is all a learning process[INDENT][INDENT]I am all for what I can learn
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-10-04
sasafrass452; Yuk:

> 
So, anything else we can try?

I am presently spinning my wheels . I have no experience in 16.04 plymouth ( systemd ) and I am in my searching/learning mode.

As to releases; there is a new release every 6 months, the 2nd year cycle is a LTS release -> 12.04, 14.04, 16.04 and to be 18.04 .

[INDENT]if I come up with something I will advise;
[INDENT][INDENT]no quit in my nature
[/INDENT][/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-04
Ok, thankyou for your continued help, it's greatly appreciated! I'll wait for the results of your research, or the upgrade next week.... whichever comes first.... Thankyou again!

> **Bashing-om said:**
> sasafrass452; Yul:


I am presently spinning my wheels . I have no experience in 16.04 plymouth ( systemd ) and I am in my searching/learning mode.

As to releases; there is a new release every 6 months, the 2nd year cycle is a LTS release -> 12.04, 14.04, 16.04 and to be 18.04 .

[INDENT]if I come up with something I will advise;
[INDENT][INDENT]no quit in my nature
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-10-06
sasafrass452; Hey .

Making a bit of progress, what have we in the default theme directory ?
```

ls -al /usr/share/plymouth/themes/ubuntu-logo

```
verify these contents.

Only one more step on the learning curve
[INDENT][INDENT][INDENT]maybe enough ?
[/INDENT][/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-07
[COLOR=#800080][/COLOR][COLOR=#800080][/COLOR]Here's what terminal says. Please note the ones in purple, as this is how it appeared in terminal. No clue what that means....

drwxr-xr-x  2 root root  4096 Aug  3 08:21 .
drwxr-xr-x 13 root root  4096 Oct  2 09:21 ..
-rw-r--r--  1 root root   204 May 10 13:56 [COLOR=#800080]password-field16.png[/COLOR]
-rw-r--r--  1 root root   778 May 10 13:56 [COLOR=#800080]password-field.png[/COLOR]
-rw-r--r--  1 root root   156 May 10 13:56 [COLOR=#800080]progress-dot-off16.png[/COLOR]
-rw-r--r--  1 root root   373 May 10 13:56 [COLOR=#800080]progress-dot-off.png[/COLOR]
-rw-r--r--  1 root root   117 May 10 13:56 [COLOR=#800080]progress-dot-on16.png[/COLOR]
-rw-r--r--  1 root root   373 May 10 13:56 [COLOR=#800080]progress-dot-on.png[/COLOR]
-rw-r--r--  1 root root  2189 May 10 13:56 [COLOR=#800080]ubuntu-logo16.png[/COLOR]
-rw-r--r--  1 root root    47 May 10 13:56 ubuntu-logo.grub
-rw-r--r--  1 root root   246 May 10 13:56 ubuntu-logo.plymouth
-rw-r--r--  1 root root  6369 May 10 13:56 [COLOR=#800080]ubuntu-logo.png[/COLOR]
-rw-r--r--  1 root root   264 May 10 13:56 ubuntu-logo-scale-2.plymouth
-rw-r--r--  1 root root 39307 May 10 13:56 ubuntu-logo-scale-2.script
-rw-r--r--  1 root root 38806 May 10 13:56 ubuntu-logo.script

> **Bashing-om said:**
> sasafrass452; Hey .

Making a bit of progress, what have we in the default theme directory ?
```

ls -al /usr/share/plymouth/themes/ubuntu-logo

```
verify these contents.

Only one more step on the learning curve[INDENT][INDENT][INDENT]maybe enough ?
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-10-07
sasafrass452; Well ...

That list is exactly as what is on a default install in my test bed . The proper files are in place . So it is but a matter of determining what calls the image file. As I have stated, I am having difficulties finding the plymouth documentation as explicitly pertains to 16.04's systemd . Anything other is the upstart system and does not cross relate !

I continue to plug away at this ->

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-11
Just wondering if you're making any progress? I'm hoping the upgrade this week will resolve this, but I'm not holding my breath....

> **Bashing-om said:**
> sasafrass452; Well ...

That list is exactly as what is on a default install in my test bed . The proper files are in place . So it is but a matter of determining what calls the image file. As I have stated, I am having difficulties finding the plymouth documentation as explicitly pertains to 16.04's systemd . Anything other is the upstart system and does not cross relate !

I continue to plug away at this ->
[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2016-10-11
sasafrass452; Sorry.

No forward progress to this time . I see so many things it "could be" that I can not see the tree for the forest .
I have not given up still look'n as I have an idea to investigate.
Setting break points and seeing what the system reports and how far it gets in the boot process may still be our best means of finding what is failing .

And Yes, if this is a bug, a new kernel may well resolve this issue.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sasafrass452 on 2016-10-11
No problem, I understand. Thankyou again for your continued help, I appreciate any input you can give me! After the upgrade, I'll post here if the issue is resolved or not.

> **Bashing-om said:**
> sasafrass452; Sorry.

No forward progress to this time . I see so many things it "could be" that I can not see the tree for the forest .
I have not given up still look'n as I have an idea to investigate.
Setting break points and seeing what the system reports and how far it gets in the boot process may still be our best means of finding what is failing .

And Yes, if this is a bug, a new kernel may well resolve this issue.
[INDENT][INDENT]sometimes I wonder[INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I am ECSTATIC to report that my splash screen is back upon upgrading to 16.10!!! WOOHOO!!!

---

