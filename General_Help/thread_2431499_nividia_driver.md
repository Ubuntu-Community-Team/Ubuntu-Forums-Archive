---
title: "nividia driver"
date: 2019-11-17
forum: General Help
---

### Post by neelk2 on 2019-11-17
iam a newbie to ubutu world coming today from windows 10 and i do not have interest to go back
i face problem with my nividia Quadro FX 4500 is old and 512mb someway ubuntu did not recognize
auto the driver and i fail to find compitable maunally and help please

---

### Post by TheFu on 2019-11-17
Sorry, I cannot help.  My Quadro issue was solved by spending $70 for a GT 1030.

To get the best help, please answer:
* which ubuntu release?  16.04?
* which DE is being used?  Gnome3, Mate, KDE, LXDE, LXQt, something else?
* which exact card?  **sudo lshw -C video** Post all the output, since it will show the driver and version of the driver.
The first 2 answers should be included in any posts here.
The last one should be modified for any specific hardware issue. We always need to know the exact, reported, version, the driver and version of the driver.  That applies to USB stuff, network stuff, audio stuff, whatever - if it is hardware we need the specific, correct, information.

We also need to know what you've already tried.  For example, with nVidia GPUs, it is common to use the nomemset grub option. Have you tried that?

---

### Post by neelk2 on 2019-11-17
thank you for your reply
use dell t5500 

153 kdevtmpfs
2165 gnome-keyring-d
2279 gnome-session-b
2497 gnome-session-c
2505 gnome-session-b
2523 gnome-shell
2569 gnome-shell-cal
3509 gnome-software
6444 gnome-terminal-

[h=2]Ubuntu 19.10[/h]display                 
       description: VGA compatible controller
       product: G70GL [Quadro FX 4500]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
        resources: irq:33 memory:f5000000-f5ffffff memory:e0000000-efffffff  memory:f6000000-f6ffffff ioport:dc80(size=128) memory:c0000-dffff

hope could help

---

### Post by oldfred on 2019-11-17
This says it uses the 304 series of driver.
[https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

I believe that the 304 driver is not supported anymore.

I have a newer GF108 [GeForce GT 620] and cannot tell difference with nVidia driver and open source nouveau driver.

Does nouveau driver not work?

---

### Post by TheFu on 2019-11-17
The current LTS is 18.04. Newer isn't better.  Often, the documentation online only gets updates for LTS versions.

Not every Ubuntu release is the same.  LTS gets 5 yrs of free support without any hassles.  Non-LTS like 19.xx or any October release only gets 9 months of support, maximum.  [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) explains more. There's a nice chart there which makes it pretty clear.

---

### Post by mörgæs on 2019-11-18
I would recommend that you stay with 19.10 but try one of the lighter buntus like Mate/Lubuntu/Xubuntu...

---

### Post by neelk2 on 2019-11-18
thank you for all 
i like ubuntu and deserve to try , i made clean install to 18.04 i working better than 19.10
and install version 304.137 in software & upates when apply chnage getback to novveau
and i find solution but hard to underatand it 
this is the 
link [https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787/43](https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787/43)
--------------
Hi!
 I have a pc with an old Geforce 6800 card and I have managed to  successfully install the 32bit Nvidia 304.137 driver for it on Lubuntu  18.04; all thanks to a community patch. Here is the procedure.
 **Install build tools**
$ sudo apt install gcc make build-essential gcc-multilib dkms mesa-utils
 **Download driver** from [https://www.nvidia.com/Download/driverResults.aspx/123708/en-us 306]("https://www.nvidia.com/Download/driverResults.aspx/123708/en-us")
 **Download patch** from [https://adufray.com/nvidia-304.137-bionic-18.04.patch 445]("https://adufray.com/nvidia-304.137-bionic-18.04.patch")
 **Extract archive, place patch into extracted folder and apply patch**
$ ./NVIDIA-Linux-x86_64-304.137.run -x
$ cd ./NVIDIA-Linux-x86_64-304.137
$ patch -p1 < nvidia-304.137-bionic-18.04.patch
 **Disable nouveau driver and reboot**
$ sudo -i
# cat << END > /etc/modprobe.d/disable-nouveau.conf
blacklist nouveau
blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist amd76_edac
options nouveau modeset=0
END
# update-initramfs -u
# reboot
 **Stop x-server**
Logout
Bring up terminal with Ctrl-Alt-F1, login
$ sudo -i
# service lightdm stop
# init 3
 **Install NVidia driver**
Ignore the first warning about preinstall failing, agree to driver  recompilation on kernel update and to configuration files update.  Reboot.
# ./nvidia-installer
# reboot
 Driver should be working now. Check with the following:
$ lshw -c video 2>&1 | grep driver
Should output"configuration: driver=nvidia"
 There is one small problem though. Apparently Nvidia driver installs  it&#8217;s own version of libvdpau, which does not work with mplayer. That&#8217;s  why we need to forcefully **reinstall libvdpau** (and  possibly need to do this on kernel update, because driver will recompile  and reinstall it&#8217;s own, non-functioning version for this library?)
$ sudo apt --reinstall install libvdpau1

------

how to do it proper. iam totally newbie but willing to learn to fix mine

---

