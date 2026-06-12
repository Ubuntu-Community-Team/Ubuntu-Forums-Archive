---
title: "Wacom intuos Tablet"
date: 2006-12-22
forum: General Help
---

### Post by Ted D. on 2006-12-22
I am trying to get my Tablet operating properly. I need the Wacom kernel source, but synaptic will not let me install it. 
I Get this message:
wacom-kernel-source:
 Depends: build-essential but it is not going to be installed
 Depends: debhelper but it is not going to be installed
How do I resolve this.?
Using Dapper with Celeron 2.4 processor.

Thanks for any help in advance.
Ted D.

---

### Post by MetalMusicAddict on 2006-12-22
Im not sure about that package but have you tried to install "wacom-tools" instead? See my sig for more Wacom info. Its needs updating but look through the thread.

---

### Post by xscd on 2006-12-23
> **Ted D. said:**
> I am trying to get my Tablet operating properly. I need the Wacom kernel source, but synaptic will not let me install it. 
I Get this message:
wacom-kernel-source:
 Depends: build-essential but it is not going to be installed
 Depends: debhelper but it is not going to be installed
How do I resolve this.?
Using Dapper with Celeron 2.4 processor.

Thanks for any help in advance.
Ted D.

**FIRST** see if you already have the kernel Wacom tablet installed. You probably do. To find it, first update the "locate" database by typing in a terminal window:

sudo updatedb

Then, when that command is done (in a few minutes or so), type:

locate wacom.ko

(wacom.ko is the kernel Wacom driver for 2.6 series kernels. If you are using an older 2.4 series kernel instead, it will be wacom.o instead of wacom.ko)

In my Ubuntu Edgy Eft installation, my wacom.ko kernel driver is at:

/lib/modules/2.6.17-10-386/kernel/drivers/usb/input/wacom.ko

If the kernel driver is already installed, you won't need to install the wacom-kernel-source package. You will only need to install the Xorg Wacom driver and the udev Wacom scripts using synaptic:

xserver-xorg-input-wacom
wacom-tools

Please refer to the following threads that explain in detail how to get a Wacom tablet working:
[http://www.ubuntuforums.org/showthread.php?t=320760&highlight=wacom]("http://www.ubuntuforums.org/showthread.php?t=320760&highlight=wacom")
[http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom]("http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom")

The reason that you can't install the wacom-kernel-source right now is because it needs a "build environment" to compile the source code, using a configure script and the GNU "make" utilities, for example. That's why your synaptic is asking you to install the packages build-essential and debhelper first. But beware, even **after** you install those packages, the wacom-kernel-source package will need at least the kernel headers for the specific kernel you are using, to refer to when the wacom-kernel-source is being built and to make sure it is built correctly. So if you want to install the wacom-kernel-source, you will not only have to install build-essential and debhelper, but the kernel headers. If you don't understand this, or don't care to do the research to learn about this process, then it might be best to rely on the kernel Wacom driver that you probably already have installed.
:)

---

### Post by Ted D. on 2006-12-29
Folks I tried settings as per MetalMusicAddict suggestions, Unfortunately, I have messed something up and X is now "crashing. I did save my xorg.conf.old but I don't know how to restore it.:-?  Don't know how to restore my old xorg.conf even in recovery mode. Need assistance, please, to get X up and running.
Ted D.

---

### Post by Ted D. on 2006-12-30
No Luck. X crashed. Eventually did a reinstall. Probably a drastic fix. But I am still a tiny person lost in the woods when it comes to linux. Thanks for your assistance, I have  done something incorrectly.
Ted D.

---

