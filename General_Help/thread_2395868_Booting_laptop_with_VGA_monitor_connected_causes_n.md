---
title: "Booting laptop with VGA monitor connected causes no output on both screens"
date: 2018-07-07
forum: General Help
---

### Post by kenshin9786 on 2018-07-07
Please excuse my noobness and somewhat bad english.

I am coming back to Linux after a long time and I remain a noob for sure. Also thanks anyone in advance!

My laptop is an HP Pavilion 15 with an AMD APU A10-5750M that comes with Radeon HD 8650G, I am running Ubuntu Mate 18.04.

I had the same problem by default with Xubuntu (can't remember if 16.04 or 14.04), but not with a freshly installed Ubuntu Mate 18.04: when I booted with a monitor connected, it just mirrored both screens so everything OK, I used the "Displays" utility and configured it the way I wanted.

The problem started some days ago, after I installed amdgpu downloaded from

[https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx)

following the instructions on

[https://support.amd.com/en-us/kb-articles/Pages/Installation-Instructions-for-amdgpu-Graphics-Stacks.aspx](https://support.amd.com/en-us/kb-articles/Pages/Installation-Instructions-for-amdgpu-Graphics-Stacks.aspx)

that is just basically extracting and running ./amdgpu-install -y and then, after seeing my laptop heating even while I was not running anything beside the file explorer, I uninstalled it just running amdgpu-uninstall.

If I turn on the laptop with the monitor connected now it doesn't show any output so I have to turn it off, disconnect the monitor, and then boot again.

Then, after Ubuntu finished starting and showing graphical output on the laptop screen, I connect my VGA monitor. Everything OK up to this point.

But when I enter the "Displays" utility the laptop screen does a weird glitch you can see here

[https://streamable.com/p8o74](https://streamable.com/p8o74) (I didn't attach the video here because it says it is an invalid file)

There I am filming the laptop screen while I am moving the "Displays" window on my external monitor. It kind of divides the laptop screen in rows, showing some output of the actual laptop screen and every other one being from the output of the external monitor.

At least that's what it seems to me.

My guess is that when I enter into "Displays" when the monitor is connected, it tries to extend and use both screens but fails and does that glitch.

Then, everytime I start Ubuntu I should check that my monitor is not connected, then even if I started with the monitor disconnected, when I enter "Displays" I know it will have that glitch, so I have to try to drag the "Displays" utility to the external monitor, and just then I would be able to configure it.

So it is kind of annoying as you would guess ](*,)

I believe it is my fault because the freshly installed Ubuntu Mate didn't have this problem.

How can I get it to mirror the screens, or at least have one screen enabled, when booting with the monitor connected?

Or how can I at least avoid the glitch I show in the video, that occurs when I enter the displays utility with my monitor connected?

I'll also post here the output of commands I think could be useful to someone who wants to help (Please keep in mind I just got these commands from an askubuntu question about "how can I know what driver am I using?", I just can try to guess what info they show 'cause of my noobness)

```
--- COMMAND ---: lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8650G]


--- COMMAND ---: find /dev -group video
/dev/fb0
/dev/media0
/dev/video0
/dev/dri/card0
/dev/dri/renderD128


--- COMMAND ---: glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: X.Org (0x1002)
OpenGL vendor string: X.Org


--- COMMAND ---: grep LoadModule /var/log/Xorg.0.log
[    44.849] (II) LoadModule: "glx"
[    44.912] (II) LoadModule: "radeon"
[    44.929] (II) LoadModule: "ati"
[    47.352] (II) LoadModule: "modesetting"
[    47.353] (II) LoadModule: "fbdev"
[    47.353] (II) LoadModule: "vesa"
[    47.997] (II) LoadModule: "fbdevhw"
[    48.578] (II) LoadModule: "fb"
[    48.578] (II) LoadModule: "dri2"
[    48.578] (II) LoadModule: "glamoregl"
[    49.444] (II) LoadModule: "ramdac"
[    50.182] (II) LoadModule: "libinput"


--- COMMAND ---: glxinfo | grep -i "vendor\|rendering"
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: X.Org (0x1002)
OpenGL vendor string: X.Org


--- COMMAND ---: ls /etc/X11/xorg.conf
ls: cannot access '/etc/X11/xorg.conf': No such file or directory


--- COMMAND ---: cat /etc/modprobe.d/*kms*
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.


--- COMMAND ---: find /etc/modprobe.d/
/etc/modprobe.d/
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/amd64-microcode-blacklist.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/intel-microcode-blacklist.conf

--- COMMAND ---: xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 16384 x 16384
eDP connected (normal left inverted right x axis y axis)
   1366x768      59.99 +  39.94  
   1280x720      59.97  
   1152x768      59.95  
   1024x768      59.95  
   800x600       59.96  
   848x480       59.94  
   720x480       59.94  
   640x480       59.94  
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1280x1024_60.00  59.89* 
HDMI-0 disconnected (normal left inverted right x axis y axis)



```

---

### Post by kenshin9786 on 2018-07-08
I don't know if it will be useful, but I put my Xorg.0.log on

[https://paste.ubuntu.com/p/DwVgBX8yzB/](https://paste.ubuntu.com/p/DwVgBX8yzB/)

---

