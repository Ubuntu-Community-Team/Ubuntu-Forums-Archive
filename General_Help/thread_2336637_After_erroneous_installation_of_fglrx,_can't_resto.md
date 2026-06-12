---
title: "After erroneous installation of fglrx, can't restore 'radeon' driver or log-in"
date: 2016-09-09
forum: General Help
---

### Post by bainespal on 2016-09-09
I foolishly ruined my installation of Ubuntu 16.04 by trying to install the proprietary driver fglrx -- the version actually intended for Ubuntu 15.10, downloaded from AMD. (The reason I thought I had to install it was because Steam wouldn't start, so I just assumed I needed the proprietary driver and I didn't take one minute to read the 16.04 release notes or anything.)

The result is a log-in loop, where I get dumped back to the log-in screen after entering my password or trying to use a guest log-in. I can access the terminal by the keyboard command **Ctrl + Alt + F2**.

After logging in to the terminal, I uninstalled and purged flgrx as described [here]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx").

I also tried several times to fix the log-in loop by moving and deleting the '.Xauthority' file, as documented by this [YouTuber]("https://youtu.be/OG4deLa_vK8"). That didn't work. Some things I read gave me the impression that the '.Xauthority' file isn't even needed in 16.04, but even when the file is definitely absent, the log-in loop persists.

I tried to switch to the LXDE desktop environment, figuring that doing so would at least give me GUI access to my system and hoping that it might overwrite whatever might be wrong. I used the command **'sudo apt-get install lubuntu-desktop**' and basically turned my computer into a still-not-working Lubuntu 16.04. I now boot to a LXDE log-in screen, but other than that, the behavior when I try to log in is the same.

I believe that either the initial installation of fglrx or some of my undocumented troubleshooting attempts have completely purged the original open source driver **radeon**. I don't know how to get it back. The word "radeon" is not the name of a [package]("http://packages.ubuntu.com/xenial/allpackages") that I can install with apt-get.

Here is the output of **sudo lshw -C display**:

```
*-display UNCLAIMED
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0000000-f001ffff ioport:1100(size=256) memory:f0040000-f005ffff
```

Notice that it says that 'display' is "UNCLAIMED". I believe this shows the problem, but I don't know exactly what it means or how to correct it.

My only remaining idea is to try installing a driver from [one]("https://launchpad.net/%7Eoibaf/+archive/ubuntu/graphics-drivers/") of the [two]("https://launchpad.net/%7Epaulo-miguel-dias/+archive/ubuntu/mesa/") PPAs, but I don't even properly know how to do that, and I've gotten myself in to too much trouble by trying things that I don't understand so far.

I really think I just need to re-install the 'radeon' driver, if anyone could tell me how to do that.

---

### Post by DuckHook on 2016-09-11
Your first task is to back up all of your important data so that you are dealing with, at most, a minor irritation. Reinstalling a pristine install of Ubuntu is not really a big deal so long as all of your data is secure.

I would frankly recommend such a reinstall at this point. You not only have a questionable driver issue, but you now have a DE layered over Ubuntu that:

[LIST=1]
[*]greatly complicates the picture, and
[*]you don't even want.
[/LIST]
Even if you successfully get radeon working again, trying to back out all of the LXDE environment will be like pulling teeth.

---

### Post by QIII on 2016-09-11
Hello!

Would you please post back the results of 

```
lsmod | grep radeon
```

and 

```
lsmod | grep amdgpu
```

(Use your cell phone to take a picture if you have to!)

These will tell us if either the radeon driver or the AMDGPU driver is loaded in the kernel.

---

### Post by Jimysbil on 2016-09-11
Try those commands:
```
sudo su
apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you have installed those drivers from a package you should run something like that too:
```
cd [COLOR="#FF8C00"]{package directory}[/COLOR]
sh [COLOR="#FF8C00"]{package name}[/COLOR].run --uninstall
```

---

### Post by bainespal on 2016-09-11
I'm thinking DuckHook probably has the right idea, since the results of **lsmod | grep radeon** and **lsmod | grep amdgpu** are both blank. Nothing happens, and the terminal prompt doesn't disappear, so it's clearly not working on something in the background. It's the same whether or not I prefix the commands with **sudo**.

I don't know how to find where my USB drive is mounted. (The physical device I just plugged, I mean.) If I can navigate to the directory for my USB drive with the terminal, I'll be able to copy over my files with the **cp** command.

I will also send the distro maintainers a photo of myself wearing a rabbit-ears headband so they can include it in the default home directory for the next LTS release, with a caption warning new Ubuntu users not to be foolish.

Thank you.

---

### Post by deadflowr on 2016-09-11
> I don't know how to find where my USB drive is mounted. (The physical device I just plugged, I mean.) If I can navigate to the directory for my USB drive with the terminal, I'll be able to copy over my files with the cp command.
On the desktop it would simply be mounted in the /media directory.

But since this seems not to be a desktop, then it's probably not mounted.
So to mount you need to know what the device listing scheme is for it.
Run ```
sudo parted -l
```
and the usb device number should be listed.
(usually it'll be something like /dev/sdc, or something like that.)
Then determine the partition number:  ie /dev/sdc1, or what have you.

Then just run the mount command:
```
sudo mount /dev/sd?# /mnt
```
replace the ? with the dev number and the #with the partition number.
You can mount it anywhere, it's just the /mnt location is empty and designed for this.

But that's a basic method of mounting.
Your device may or may not need an extra option, or two, added to the mount command, but I would not know what.
(Others might, so perhaps post anything you can about the usb' output from the parted command. Might be helpful)

After that then it'll be mounted and you can start copying.

---

### Post by DuckHook on 2016-09-11
We could try reactivating/reinstalling radeon/amdgpu (in your case, it is  highly probable to be radeon), but the process can be somewhat convoluted and difficult from the command line. I think the *easiest* course of action at this point is to backup and reinstall. However, trying to get everything working again would be very educational (if that sort of thing floats your boat). Either way, the first thing is to backup, which *deadflowr* has already provided instructions for.

---

### Post by bainespal on 2016-09-12
> **deadflowr said:**
> 
But since this seems not to be a desktop, then it's probably not mounted.
So to mount you need to know what the device listing scheme is for it.
Actually, it is a desktop. But regardless, I was able to mount the USB drive and copy over my files using your instructions. Thank you.

[QUOTE=DuckHook]
We could try reactivating/reinstalling radeon/amdgpu (in your case, it  is  highly probable to be radeon), but the process can be somewhat  convoluted and difficult from the command line. I think the *easiest* course of action at this point is to backup and reinstall.
[/QUOTE]
That would help me access some data I've got in an SQL database. (I've copied the database to the USB, so it's not that important.) If you don't mind if I'm only able to check the forum a couple times a day, I'd follow along with your instructions.

Either way, thank you, very much. I'm sorry I took so long to reply today.

---

### Post by DuckHook on 2016-09-13
> **bainespal said:**
> I'm sorry I took so long to reply today.No problem. We're not going anywhere. Take as much time as you need.> I was able to mount the USB drive and copy over my files using your instructions.This is good news. At most you are now dealing with a minor irritation since all your data is safe. Please do make sure that you can read all of those files on the USB stick/drive. A backup is only as good as its ability to be restored.> That would help me access some data I've got in an SQL database… I'm only able to check the forum a couple times a day…If this is not a production box and is not critical to your workflow then we can plod along hoping for a solution.

Firstly, let's see if radeon is even present in your system:```
locate radeon | grep ko
``````
apt-cache policy libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```Let's also see if radeon is not just blacklisted:```
ll /etc/modprobe.d
``````
cat /etc/modprobe.d/blacklist.conf
```How did you install the fglrx drivers that you downloaded from AMD? Through the install script? Or did you convert it into a deb file and install from software center/synaptic?

---

### Post by bainespal on 2016-09-13
> **DuckHook said:**
> \How did you install the fglrx drivers that you downloaded from AMD? Through the install script? Or did you convert it into a deb file and install from software center/synaptic?

The 15.10 version from thus [page]("http://support.amd.com/en-us/download/linux"). I didn't create a deb, but then after this failed initially (before I restarted and discovered the problem) I may have tried installing fglrx through the repositories too. (Synaptic package manager and/or apt-get.) I can't remember whether or not I went through with that idea, though, sorry.

**locate radeon | grep ko**:

```

/lib/modules/4.4.0-31-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
/lib/modules/4.4.0-31-generic/kernel/drivers/video/fbdev/aty/radeonfb.ko
/lib/modules/4.4.0-34-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
/lib/modules/4.4.0-34-generic/kernel/drivers/ video/fbdev/aty/radeonfb.ko
/lib/modules/4.4.0-36-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
/lib/modules/4.4.0-36-generic/kernel/drivers/video/fbdev/aty/radeonfb.ko

```

**apt-cache policy libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core**:

```

libgl1-mesa-dri:
  Installed: 11.2.0-ubuntu2.1
  Candidate: 11.2.0-1ubuntu2.1
  Version table:
 *** 11.2.0-1ubuntu2.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     11.2.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
xserver-xorg-core:
  Installed: 2:1.18.3-1ubuntu2.3
  Candidate: 2:1.18.3-1ubuntu2.3
  Version table:
 *** 2:1.18.3-1ubuntu2.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.18.3-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

**ll /etc/modprobe.d**:

```
total 72
drwxr-xr-x   2 root root  4096 Sep  4 08:20 ./
drwxr-xr-x 148 root root 12288 Sep  4 08:22 ../
-rw-r--r--   1 root root  2507 Jul 30  2015 alsa-base.conf
-rw-r--r--   1 root root   325 Mar 13  2016 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Mar 13  2016 blacklist.conf
-rw-r--r--   1 root root   115 Sep  3 22:58 blacklist-fglrx.conf
-rw-r--r--   1 root root   210 Mar 13  2016 blacklist-firewire.conf
-rw-r--r--   1 root root   697 Mar 13  2016 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Jul 30  2015 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Aug 14 20:05 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Mar 13  2016 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Mar 13  2016 blacklist-watchdog.conf
-rw-r--r--   1 root root   390 Apr 12 06:06 fbdev-blacklist.conf
-rw-r--r--   1 root root   347 Mar 13  2016 iwlwifi.conf
-rw-r--r--   1 root root    16 Mar  8  2009 libpisock9.conf
-rw-r--r--   1 root root   104 Mar 13  2016 mlx4.conf
-rw-r--r--   1 root root    30 Mar  3  2016 vmwgfx-fbdev.conf

```

And here is the file **blacklist.conf** from **/etc/modprobe.d**:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by DuckHook on 2016-09-13
We are making good progress. You already have the requisite radeon drivers installed. They just seem to be choking on something that prevents them from loading at boot. To cover off the repository angle, please do:```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
```If you installed drivers from a script, this command may result in nothing. If so, please report it as so just to confirm. We should also see what is in:```
cat /etc/modprobe.d/blacklist-fglrx.conf
```

---

### Post by bainespal on 2016-09-15
**sudo apt-get remove --purge xorg-driver-fglrx fglrx***:
```

Reading package lists... Done
Building dependency tree
Reading state information.... Done
Note, selecting 'fglrx-pxpress' for glob 'fglrx*'
Note, selecting 'fglrx-updates' for glob 'fglrx*'
Note, selecting 'fglrx' for glob 'fglrx*'
Package 'fglrx-glx' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
Package 'fglrx' is not installed, so not removed

```
Does this reply mean that I need to be connected to the Internet first?


**cat /etc/modprobe.d/blacklist-fglrx.conf**:
```

! Advanced Micro Devices, Inc.
! radeon conflicts with AMD Linux Graphics Driver
blacklist radeon
blacklist amdgpu

```

(I think those first characters on the first two lines are exclamation points. It's hard to be certain because the resolution on my monitor is a little off, and I couldn't copy the file the same I did before for blacklist.conf. For some reason it shows up in the mounted USB in the broken terminal computer, but not when I plug the USB back in here. I tried it twice. But that's not really relevant, in any case.)

---

### Post by Jimysbil on 2016-09-15
I think you should check [this]("http://askubuntu.com/questions/510162/unable-to-completely-purge-fglrx") out.
My theory is you have some fglrx module left in your kernel and it is breaking your terminal.
As your *blacklist-fglrx.conf* shows, you have all the other amd/ati drivers disabled during startup.You could try to remove (or move) it and you see if you have different results after a reboot.

---

### Post by DuckHook on 2016-09-15
> **bainespal said:**
> …Does this reply mean that I need to be connected to the Internet first?…you should always be connected when running *apt*. It doesn't work properly otherwise.> **cat /etc/modprobe.d/blacklist-fglrx.conf**:
```

! Advanced Micro Devices, Inc.
! radeon conflicts with AMD Linux Graphics Driver
blacklist radeon
blacklist amdgpu

```…This confirms that you still have fglrx drivers installed and conflicting with your radeon. Instead of further tinkering (with attendant risk of further breakage), find the directory that you downloaded and expanded the original script to. There should be an uninstall script. Run that and it should remove the fglrx driver. Check for blacklist-fglrx.conf afterwards. If it is gone, reboot and see if radeon comes up naturally.

---

### Post by bainespal on 2016-09-21
> **DuckHook said:**
> This confirms that you still have fglrx drivers installed and conflicting with your radeon. Instead of further tinkering (with attendant risk of further breakage), find the directory that you downloaded and expanded the original script to. There should be an uninstall script.

You're right. There is an uninstall script, in a permission-locked folder in the directory where I unpacked the installer initially. Unfortunately, getting the uninstall script to work is not a simple matter. Besides playing with **chmod** for permissions problems, after running the script the output says to check the output of a log file. When I viewed that file, it had only one line that basically named the driver, and no other output. The log-in loop was not fixed and the contents of **blacklist-fglrx.conf** were not changed.

It's time for me to let go an simply reinstall 16.04, because circumstances are making it very difficult for me to use my internet connection with my disabled desktop while also using my other computer. (Wifi is down at the house, etc.) And I don't really have the time. I'm sorry for abandoning ship after asking you to help me, but thank you.

**For anyone reading this thread trying to fix a similar problem, if most of this thread was relevant to you, definitely look into whether or not you can use the downloaded package's uninstall script.** (The permissions are so wacky with that subfolder that I can't even use the *ls* command when I navigate to be inside of it using *sudo*.)

---

### Post by DuckHook on 2016-09-21
There is one more thing you can try. It's a dirty option because it leaves all sorts of loose ends around, but if the alternative is reinstalling altogether, then you really haven't anything to lose.

[LIST=1]
[*]```
sudo rm -f /etc/modprobe.d/blacklist-fglrx.conf
```
[*]```
sudo nano /etc/modprobe.d/blacklist.conf
```
[*]Add the line:```
blacklist fglrx
```
[*]Save, exit nano, reboot.
[/LIST]
This deletes the offending blacklist file, then blacklists the fglrx driver instead. It's quick, dirty and may bork your system even further, but hey&#8230; you are prepared to nuke it anyway&#8230;

---

