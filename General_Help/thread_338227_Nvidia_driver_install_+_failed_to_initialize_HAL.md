---
title: "Nvidia driver install + failed to initialize HAL"
date: 2007-01-14
forum: General Help
---

### Post by Snoochie on 2007-01-14
Hello,

First, if this is the inappropriate sub-forum, please move this thread to the relevant place.

As to my problem:

I'm not a newbie and have been using various distros for a long time. Yet, I have come across a problem that I am unable to solve.

I have installed Edgy on a new machine, AMD64 M2V K8T890 chipset and successfully configured and compiled audio and network drivers. However, I'm unable to install the graphic driver.

If I try to install via Add/Remove > I get a successful install message. After enabling the driver and restarting gdm I get to a black screen. If I do not restart gdm but reboot, I get to xserver error - it is disabled. Manually running dpk-reconfigure xserver-xorg works. I must use nv and not nvidia. But when I boot into desktop, no nvidia driver is installed.

Alternatively, if I try to stop the gdm, I also get a black screen.

Alternatively, if I switch to telinit 1, I get the console. Installing the Nvidia driver from here is accompanied by a message that it is not advisable to install in runlevel 1. After successfully installing the driver and restarting gdm, I get the 'failed to initialize HAL' error.

After reboot, again, the same problem with xserver. It is disabled until I manually configure the xorg. When I reach desktop, there is no HAL error - but no nvidia driver either.

Trying the driver suggested in Add/Remove does not help. Trying the latest driver from Nvidia site does not help.

I'm baffled.

A side question that nags me concerns the runlevels. Obviously, I'm unable to stop the server in runlevel 3 for the driver install - and doing it from runlevel 1 does not work.

Any ideas?

Snoochie

---

### Post by hal10000 on 2007-01-14
Did you install the nvidia driver from nvidia's website or from the ubuntu disribution (package linux-restricted-modules-yourkernel)?
THose from the nvidia website are running on my system and are fine, but require the packages build-essential and kernel-headers to be installed.
But both should work. Maybe you just have to install the nvidia-glx package.
[COLOR="Red"]sudo apt-get nvidia-glx[/COLOR]

---

### Post by Snoochie on 2007-01-14
Hello,
Thanks for the quick reply.
I tried them all, from ubuntu and nvidia site.
Essentials and headers installed.
Snoochie

---

### Post by tchoklat on 2007-01-15
try the envy package to install the latest nvidia drivers

---

### Post by Snoochie on 2007-01-16
Hello,

Could you please elaborate on the envy package?

I got over the HAL problem.
But I cannot install the drivers, for the love of Goddess...

I installed linux-restricted-amd64 - all of them.
I installed nvidial-kernel-module - which reads 8774 version through Synaptic.

Stopped gdm, sh driver, installed. Restart gdm.

Works! Nvidia splash.

Reboot...

X disabled. Error - kernel driver 7184 does not match ... 8774.

The same thing for any version, be it 8774, 8776 etc... I must change nvidia to nv to be able to reach desktop. But then I do not have the driver, even if it's listed when I click Add/Remove.

Installation via GUI does not work. Trying nvidia-glx-config AFTER supposedly successful installation results in error - no nvidia installed...

A real bugger this one.

I figure this has got to do with mismatch between kernel driver 7184 and nvidia driver - whichever it is. But there's no reason for that to be. I used default generic kernel during install.

My card is 7600GT - definitely not the legacy one.

I did not install nor have installed the 7184 driver. So I'm really buggered here.

I have successfully installed Ubuntu / Kubuntu many times, compiled sources, played with muck, but this one really beats me.

Cheers and thanks for all the help.

Snoochie

---

### Post by hal10000 on 2007-01-16
> X disabled. Error - kernel driver 7184 does not match ... 8774
This is the reason: Somewhere on your system there must be an older 7184 part of nvidia software (e.g. nvidia-glx, or the kernel module nvidia.ko itself)
Change your /etc/X11xorg.conf Driver from "nv" to "nvidia". Then your xserver will crash upan next restart. Then open the file /var/log/Xorg.0.log and look through the files content. I'm sure you will find some 7184 lines.

I had this problem some months ago when I updated my nvidia drivers. I had not cleanly removed some files.

---

### Post by tchoklat on 2007-01-16
[B]see here:

[http://tuxicity.wordpress.com/2006/12/22/install-the-latest-nvidia-driver-with-envy-in-kubuntu/](http://tuxicity.wordpress.com/2006/12/22/install-the-latest-nvidia-driver-with-envy-in-kubuntu/)
[/B]

---

### Post by kvonb on 2007-01-16
Follow these instructions here:

[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

Use Step2/Option2 ONLY!

It sounds like the built in NV module is getting in the way, try this:

sudo gedit /etc/default/linux-restricted-modules-common
add:
[SIZE=-1]DISABLED_MODULES="nv"[/SIZE]
to the end, save, exit, reboot.

But I would STRONGLY recommend that you follow the instructions in the link I give above, keeping in mind that you will need the AMD64 version.

Regards, KEv :)

---

### Post by Snoochie on 2007-01-17
Hello,

Mysterious are the ways of Ubuntu!

I tried the Step 2 / Option 2 and it worked excellent!!!

Nvidia drivers up and purring! Excellent help people! Be blessed.

Cheers!!!!
Snoochie

---

