---
title: "HDMI connection problem"
date: 2017-01-07
forum: General Help
---

### Post by cest2 on 2017-01-07
Hello, my PC is connected to a monitor via VGA cable. I recently tried to connect a second monitor, a FULL HD Television, using an HDMI cable. Using Ubuntu everything works fine but when I boot Lubuntu the TV goes black and displays the message "No signal" just after the loading screen, as soon as the desktop is loaded. Can anybody please help me? My video card is an MSI Radeon R5 230 1GB that I just plugged in 2 days ago without installing any additional software apart from the regular ones of the system. Thank you!

---

### Post by DuckHook on 2017-01-07
More info please.

[LIST=1]
[*]Are you dual booting, or do you have Lubuntu as an added optional DE on the Ubuntu install?
[*]Are you running both monitors side-by-side or mirroring?
[*]Are you still getting output on your VGA monitor in Lubuntu?
[*]You added nothing in Lubuntu, but did you add or configure anything in Ubuntu?
[/LIST]
Assuming that you have a working VGA monitor in Lubuntu, please post the results of the following:```
lspci -vk | grep -iA20 vga
``````
xrandr
``````
cat /etc/default/grub
``````
sudo apt install read-edid && sudo get-edid | parse-edid
```

---

### Post by cest2 on 2017-01-08
Hi, I'm dual booting. I didn't get to configure anything in Ubuntu, which is actually missing updates because I did not use it for more than a month. Monitors are side by side in Ubuntu and mirrored in Lubuntu, but that's the default behavior as I configured nothing. My VGA monitor is still receiving signal in both Lubuntu and Ubuntu. My VGA monitor resolution is 1440x900 while the TV is 1920x1080.

**lspci -vk | grep -iA20 vga**
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos PRO [Radeon HD 7450] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Caicos PRO [Radeon HD 7450]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe8c0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at c000 [size=256]
    Expansion ROM at fe8a0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon


01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Caicos HDMI Audio [Radeon HD 6400 Series]
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


02:00.0 Ethernet controller: Qualcomm Atheros Attansic L1 Gigabit Ethernet (rev b0)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
```

**xrandr**
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 16384 x 16384
HDMI-0 connected primary (normal left inverted right x axis y axis)
   1920x1080     60.00 +  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02  
   1360x768      60.02  
   1152x864      59.97  
   1280x720      59.81    60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900      59.89*+  74.98  
   1152x864      75.00  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    60.00  
   720x400       70.08 

```

**cat /etc/default/grub**
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

**sudo apt install read-edid && sudo get-edid | parse-edid**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
read-edid is already the newest version (3.0.2-1).
The following packages were automatically installed and are no longer required:
  libjansson4 libspeechd2 libxml++2.6-2v5 libxnvctrl0 linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic
  linux-headers-4.4.0-42 linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic
  linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-43-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-47-generic linux-image-4.4.0-51-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-43-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-47-generic linux-image-extra-4.4.0-51-generic screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up grub-pc (2.02~beta2-36ubuntu3.6) ...
/var/lib/dpkg/info/grub-pc.config: 1: /etc/default/grub: &#65279;#: not found
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
      dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-57-generic; however:
  Package linux-image-extra-4.4.0-57-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.57.60); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                        Setting up linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-53-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-53-generic:
 linux-image-extra-4.4.0-53-generic depends on linux-image-4.4.0-53-generic; however:
  Package linux-image-4.4.0-53-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-53-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 grub-pc
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-generic
 linux-generic
 linux-image-4.4.0-53-generic
 linux-image-extra-4.4.0-53-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cest2 on 2017-01-08
Forgot to mention: I use Gnome Flashback Metacity DE in Ubuntu and LXDE (the default one) in Lubuntu.

---

### Post by DuckHook on 2017-01-09
Since installing Lubuntu, have you run?:```
sudo apt update
```If so, then your Lubuntu install is incomplete or corrupted. Your attempt to install read-edid shows that:

[LIST=1]
[*]It is already installed, and
[*]Your package management system is broken.
[/LIST]
Since this is a new install, something has happened to break things. Did you try any procedures or Googled instructions before posting on these forums? If so, what were they? If not, then I suggest booting with a Lubuntu LiveUSB and seeing if both monitors are visible.

Why did you install Gnome flashback Metacity in Ubuntu? This is not the default. What version of Ubuntu are you running? What driver are you using in Ubuntu?

Before trying to fix the video in Lubuntu, it is important to have a complete system installed. Based on the output from the last command I doubt that you have a proper system right now.

---

### Post by cest2 on 2017-01-09
> **DuckHook said:**
> Since installing Lubuntu, have you run?:```
sudo apt update
```If so, then your Lubuntu install is incomplete or corrupted.
Yes I did.

> **DuckHook said:**
> 
Did you try any procedures or Googled  instructions before posting on these forums?

No.

> **DuckHook said:**
> 
If  not, then I suggest booting with a Lubuntu LiveUSB and seeing if both  monitors are visible.

I'll try to do that. I suppose a LiveCD would be fine as well, right?

> **DuckHook said:**
> 
[LIST=1]
[*]Your package management system is broken. 
[/LIST]

After I installed KStars I started receiving an error message during the "System Update" procedure. The message is saying that a package fails to install. I removed KStars but the problem persists.

> **DuckHook said:**
> 
Why did you install Gnome flashback Metacity in Ubuntu?

Because I prefer Gnome to Unity.

> **DuckHook said:**
> 
What version of Ubuntu are you running?

16.04 LTS

> **DuckHook said:**
> 
What driver are you using in Ubuntu?

I'll have to check that once I arrive at home. I'll also have to find out how to do that, I'm not a big expert of Linux :)

> **DuckHook said:**
> 
Before trying to fix the video in Lubuntu, it is important to have a complete system installed. Based on the output from the last command I doubt that you have a proper system right now.
Any suggestion is more than welcome :) Thank you very much for your help! \\:D/

---

### Post by DuckHook on 2017-01-09
> **cest2 said:**
> I'll try to do that. I suppose a LiveCD would be fine as well, right?Unfortunately, Lubuntu no longer fits on a CD. I believe the last version that could fit was 14.04.1. Even 14.04.2 broke the CD barrier, which is a shame, considering that one of its attractions is its ability to run on old HW that may only pack a CD drive and cannot boot from USB.> The message is saying that a package fails to install. I removed KStars but the problem persists.Ouch. You tried to install a KDE app which would have dragged in practically the whole KDE environment. This seemingly simple action turned your Lubuntu install into a hybrid Lubuntu/Kubuntu install. It's no wonder that dpkg got gummed up. You are new to the 'buntu's so your mistake is more than understandable, but you should be aware that it is a bad idea to mix Desktop Environments for exactly the reason that you are experiencing now.> Because I prefer Gnome to Unity.…which implies that you did exactly the above to your Ubuntu install as well and now have a hybrid Unity/Gnome DE. Unity and Gnome are more compatible, which is likely why you are not experiencing issues there, but the install has been made more fragile nonetheless. The usual way to run the Gnome DE is to install Ubuntu-Gnome, which installs a clean version of Gnome completely free of Unity. But since it's working, you should just leave it be for now.> I'll also have to find out how to do that…Running from your Ubuntu install, please post output of:```
sudo lspci -vk | grep -iA15 vga
```> Any suggestion is more than welcome…At this point, I strongly suggest simply re-installing Lubuntu. By installing kstars, you dragged in so many KDE elements that it would be laborious and impractical to try backing them all out. By your own description, this is a relatively new install. I assume this also means that you don't have a lot of data on this one yet. Therefore, it will be least painful if you back up what little data there is and simply reinstall Lubuntu. If your hardware is sufficiently powerful, you may wish to consider Kubuntu, as you seem to want kstars. Be aware, however, that Kubuntu requires more powerful components, quite similar to Unity, which may not fit your situation.

In future, please be careful of what apps you install. The primary advantage of Lubuntu is it's light resource requirements and simplicity. It is otherwise rather plain and ugly. Therefore, you don't want to install apps that break that light weight and simplicity, else you are better off installing the slicker DE to begin with.

---

### Post by cest2 on 2017-01-10
**sudo lspci -vk | grep -iA15 vga**
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos PRO [Radeon HD 7450] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Caicos PRO [Radeon HD 7450]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe8c0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at c000 [size=256]
    Expansion ROM at fe8a0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]

```

> **DuckHook said:**
> Unfortunately, Lubuntu no longer fits on a CD.
Then I'll use a DVD :) I'll get it from here (there are 2 links on the top-left): [http://lubuntu.net/](http://lubuntu.net/)

Thank you for all the tips and the explanations, I learned a lot and I intend to reinstall Lubuntu and replace my current Ubuntu with Ubuntu-Gnome (which I didn't know it exists :D). Actually, the reason I'm using Lubuntu si that Ubuntu got slower and slower, and maybe I start understanding why :)

---

### Post by HermanAB on 2017-01-10
Howdy,

As far as I know, LXDE only talks to the screen at login, therefore one cannot hot swap a screen with Lubuntu.

Plug the screen in, then log out and log in again and it should work.

---

### Post by cest2 on 2017-01-10
**@Herman:** thank you, it works only as long as I stay logged out. As soon as I log back in, the TV goes black.
**@DuckHook:** I used a Live DVD and everything went fine! The only problem was that the TV was selected as main monitor, while I wanted the other way around :D

I suppose the only thing left to do is reinstall Lubuntu, since apparently there's no easy way to fix it. Thank you both for your help, I really appreciate it, you helped me understand what was going on and what to do! Thanks!

---

### Post by DuckHook on 2017-01-10
> **cest2 said:**
> **@Herman:** thank you, it works only as long as I am logged out. As soon as I log back in, the TV goes black.
**@DuckHook:** I used a Live DVD and everything went fine! The only problem was that the TV was selected as main monitor, while I wanted the other way around :D
Selecting main monitor is easily solved through changing the settings. The main take-away is that LiveDVD works. I still recommend a complete reinstall. At this point, we simply don't know what config components have been changed or broken by dragging in KDE components. The fact that the LiveDVD works also bodes well for this strategy.

Please note that you have a broken package management system too. While it may be a separate issue from video, that will ultimately need fixing, else you can't update your system.

Last (but far from least), we just don't know what else is broken. It's your call whether you wish to spend your time tracking down everything that may eventually crop up, or whether you want to spend the time now to just reinstall. My last Lubuntu install took less than an hour. I suspect that you've already spent more time than that wrestling with this video issue alone.

---

### Post by cest2 on 2017-01-21
Hi there, sorry for replying with so much delay but I didn't manage to keep up with all the things I'm dealing lately :D

Thank you very much, I'll follow your advice and do a clean install. I would just need another few pieces of advice, if possible: is there any way I can spot KDE apps so that I avoid installing them? I would like to use Kdenlive, what would be the best solution? Is there a KDE version of Lubuntu or Ubuntu? Thank you!

---

### Post by DuckHook on 2017-01-21
> **cest2 said:**
> &#8230;is there any way I can spot KDE apps so that I avoid installing them?
Unfortunately, there is no consistent way. Many developers will helpfully name their KDE apps starting with a "K", but others will not. It takes a little time and research to figure out how many dependencies you will be dragging in with any given app. Further instructions below.
> I would like to use Kdenlive, what would be the best solution? Is there a KDE version of Lubuntu or Ubuntu?
KdenLive, like Kstars, is a KDE app. In this case, the "K" tells you it's a KDE app.

You appear to like KDE apps. If so, then I would suggest installing Kubuntu, which is the KDE flavour of Ubuntu. Everything will then be consistent from the beginning, and you shouldn't run into compatibility issues with any of the "K" apps that you like.

There is nothing really odd or difficult about the KDE environment. Many people like it and use it, and Kubuntu is a well-established official flavour of Ubuntu that has been around a long time and is well supported. If your HW is relatively recent, I think you will be quite happy with it.

If using Kubuntu, and you want to keep it relatively clean and default, then you will have the opposite issue where installing a gnome or gtk app will drag in a ton of dependencies that are not native to KDE. There is no "solution" to these sorts of issues. You either have to find some native KDE app that does the same thing, or you have to live with more bloat on your system for the sake of the one app that you want. Occasionally, the app will drag in not only bloat, but so many dependencies and configurations that it will break something on your Kubuntu desktop.

An easy way to tell what dependencies any app needs is:```
apt-cache depends name_of_pkg
```Then compare this to the output of:```
apt-cache depends --installed name_of_pkg
```This shows you what missing dependencies will be dragged in. My output from a relatively pristine Lubuntu install for both commands is as follows:```
duckhook@Lubuntu:~$ apt-cache depends kdenlive
kdenlive
  Depends: ffmpeg
    ffmpeg:i386
  Depends: kded5
  Depends: kdenlive-data
  Depends: kinit
  Depends: kio
  Depends: melt
  Depends: oxygen-icon-theme
    oxygen5-icon-theme
  Depends: qml-module-qtquick2
  Depends: libc6
  Depends: libkf5archive5
  Depends: libkf5bookmarks5
  Depends: libkf5completion5
  Depends: libkf5configcore5
  Depends: libkf5configgui5
  Depends: libkf5configwidgets5
  Depends: libkf5coreaddons5
  Depends: libkf5dbusaddons5
  Depends: libkf5guiaddons5
  Depends: libkf5i18n5
  Depends: libkf5iconthemes5
  Depends: libkf5itemviews5
  Depends: libkf5jobwidgets5
  Depends: libkf5kiocore5
  Depends: libkf5kiofilewidgets5
  Depends: libkf5kiowidgets5
  Depends: libkf5newstuff5
  Depends: libkf5notifications5
  Depends: libkf5notifyconfig5
  Depends: libkf5plotting5
  Depends: libkf5service-bin
  Depends: libkf5service5
  Depends: libkf5solid5
  Depends: libkf5textwidgets5
  Depends: libkf5widgetsaddons5
  Depends: libkf5xmlgui5
  Depends: libmlt++3
  Depends: libmlt6
  Depends: libqt5core5a
  Depends: libqt5dbus5
 |Depends: libqt5gui5
  Depends: libqt5gui5-gles
  Depends: libqt5network5
 |Depends: libqt5quick5
  Depends: libqt5quick5-gles
  Depends: libqt5script5
  Depends: libqt5svg5
  Depends: libqt5widgets5
  Depends: libqt5xml5
  Depends: libstdc++6
  Recommends: dvdauthor
  Recommends: dvgrab
  Recommends: frei0r-plugins
  Recommends: genisoimage
  Recommends: recordmydesktop
  Recommends: swh-plugins
  Suggests: khelpcenter
```
```
duckhook@Lubuntu:~$ apt-cache depends --installed kdenlive
kdenlive
    ffmpeg:i386
    oxygen5-icon-theme
  Depends: libc6
  Depends: libqt5core5a
  Depends: libqt5dbus5
 |Depends: libqt5gui5
  Depends: libqt5network5
  Depends: libqt5svg5
  Depends: libqt5widgets5
  Depends: libstdc++6
  Recommends: genisoimage
```
You can see that kdenlive requires a mess of additional dependencies in order to run in Lubuntu. Keep in mind that many of these packages drag in even further dependencies. Another fast and dirty method is to use the -s switch, which will do a simulated install. My results were:```
duckhook@Lubuntu:~$ apt install -s kdenlive
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Also keep in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dvdauthor dvgrab ffmpeg frei0r-plugins kded5 kdenlive-data kinit kio kwayland-data kwayland-integration
  libavdevice-ffmpeg56 libdbusmenu-qt5 libdc1394-22 libdouble-conversion1v5 libfam0 libfftw3-single3 libgavl1
  libgtkglext1 libjasper1 libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5 libkf5bookmarks-data
  libkf5bookmarks5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin
  libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5
  libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5 libkf5gpgmepp5
  libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5
  libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5
  libkf5kiofilewidgets5 libkf5kiontlm5 libkf5kiowidgets5 libkf5newstuff-data libkf5newstuff5 libkf5notifications-data
  libkf5notifications5 libkf5notifyconfig-data libkf5notifyconfig5 libkf5plotting5 libkf5service-bin
  libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5
  libkf5sonnetui5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libmlt++3 libmlt-data libmlt6 libmovit4
  libopencore-amrnb0 libopencore-amrwb0 libopencv-highgui2.4v5 libopencv-objdetect2.4v5 libopencv-video2.4v5
  libpangox-1.0-0 libphonon4qt5-4 libpolkit-qt5-1-1 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5script5
  libqt5waylandclient5 libqt5x11extras5 libqt5xml5 libquicktime2 libsox-fmt-alsa libsox-fmt-base libsox2 libvoikko1
  melt oxygen-icon-theme oxygen5-icon-theme qml-module-qtquick2 qtwayland5 recordmydesktop sonnet-plugins swh-plugins
&#8230;
```
As you can see, pretty nasty.

You may wish to consider the following alternatives:

[LIST=1]
[*]As already mentioned, install Kubuntu. Although it is a heavyweight flavour, it will give you tons of functionality.
[*]If you want a light and clean flavour for everyday use, but Kubuntu for those occasions when you need KDE apps, then dual boot with Lubuntu and Kubuntu. You could even multiboot with Ubuntu-gnome for a third flavour that confines all the Gnome bloat.
[*]If your system is powerful enough, run Kubuntu in a VM inside Lubuntu, or vice versa. In some ways, this is the most elegant solution since you can have as many VMs as you like.
[/LIST]
Any of the above will work to keep various Desktop dependencies and configs from clobbering each other.

Let us know how it goes!

---

### Post by cest2 on 2017-01-30
Hi there, thank you very much for all the useful info! I ended up with a dual boot of Kubuntu and Lubuntu :)

If I may ask, what is your opinion about the Appimage of Kdenlive in Lubuntu? I just recently found out there is such a possibility, but I am not sure I fully understand its characteristics ^_^

Anyway, thank you for all the support, without your help I would have probably kept doing the same mistakes :oops:

---

### Post by DuckHook on 2017-01-30
> **cest2 said:**
> I ended up with a dual boot of Kubuntu and Lubuntu…
Congratulations. I hope that it will be smooth sailing for you from now on.
> …what is your opinion about the Appimage of Kdenlive in Lubuntu? I just recently found out there is such a possibility, but I am not sure I fully understand its characteristics…
Appimages, snaps, VMs, LXC/LXD are all similar containment strategies that by varying degrees try to keep an app (or DE or whole OS) safely fenced within its own running space and separated from the host OS. This has many advantages, only one of which is what earlier plagued your install: it reduces the danger of incompatible configurations clobbering your host OS. Some of them, like VMs and LXC/LXD have the further advantage of being highly contained and therefore highly secured&#8213;this being one of their primary goals. In the case of appimages and snaps, the amount of containment is not very high, so the security aspects are rather poor, but that's not what they were designed for&#8213;they were designed to run apps with a mess of oddball dependencies without having to drag those dependencies into your host OS.

Full disclosure: while I've used VMs for years and have seriously experimented with containers (LXC/LXD), I haven't started on appimages or snaps. My knowledge about them is all second-hand and hearsay. However, on the surface, this would seem to be what you are looking for. However, I've often said that, when it comes to my production box, my overriding principle is KISS. Since you have Kubuntu already installed, why do you want to install a KDE app into Lubuntu, even if it is sufficiently segregated? Kdenlive is a serious app that makes serious use of your audio/video subsystem. I would want it running on libraries and configs that are native to KDE, and that's Kubuntu.

However…
> …I would have probably kept doing the same mistakes…
Another forum member on another thread said: "in order to become experienced, one needs experiences." I believe that mistakes are what keep us learning and growing. In this regard, if you are curious about the Kdenlive appimage, are fully backed up, and are prepared to reinstall if things get messed up, then why not?

One cannot get to new and interesting places by standing still.

---

### Post by cest2 on 2017-02-05
Hi, I agree with you but for the moment I think I'll stick with Kdenlive in Kubuntu because in this period I'm having little free time. You have my gratitude for both the help and the explanations, I hope life will reward you well =d> Best to you, thanks! ):P

---

### Post by DuckHook on 2017-02-05
Good Luck and Happy Ubuntu-ing!

---

### Post by cest2 on 2017-02-05
Thank you!

---

