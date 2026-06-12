---
title: "Does Wayland work on Ubuntu 22.04 LTS with an NVidia GPU?"
date: 2023-05-14
forum: General Help
---

### Post by John Nagle on 2023-05-14
I don't get the Wayland option at login on 22.04 LTS. Just "Ubuntu" or "Unity". This is on a machine with an NVidia 640. NVidia drivers is 470 ("proprietary, tested", "This device is using the recommended driver"). Google search for "ubuntu 22.04 wayland nvidia" turns up much contradictory information. It's clear that there have been serious problems in the past with NVidia vs. Wayland, and Weyland has been disabled for some platforms. What's the current status?

I tried editing **custom.conf:**

```
[daemon]
# Uncomment the line below to force the login screen to use Xorg
#WaylandEnable=false
WaylandEnable=true
```

No effect.

---

### Post by MAFoElffen on 2023-05-15
On mine, which is Ubuntu LTS 22.04.2
```

nfiguration'
       product: GF119M [Quadro NVS 4200M]
       vendor: NVIDIA Corporation
       configuration: driver=nvidia latency=0
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
mafoelffen@Mikes-ThinkPad-T520:~$ echo $XDG_CURRENT_DESKTOP
ubuntu:GNOME
mafoelffen@Mikes-ThinkPad-T520:~$ echo $XDG_SESSION_TYPE
wayland

```
When I select "Ubuntu on Wayland". It also has "Ubuntu on Xorg"...

---

### Post by John Nagle on 2023-05-15
[https://i.ibb.co/w4b1ngz/unityselection.png](https://i.ibb.co/w4b1ngz/unityselection.png)
Those are the available options. No Wayland option.

[https://i.ibb.co/RHvrTsX/ubuntudetails.png](https://i.ibb.co/RHvrTsX/ubuntudetails.png)
System details.

Recheck:

> echo $XDG_SESSION_TYPE
x11

So, running X11, not Wayland.

There really is no Wayland option. Why?

---

### Post by MAFoElffen on 2023-05-16
I don't know yet..

What is would suggest, is to post the output of this within CODE Tags
```

ls -l /usr/share/xsessions/ | awk '{print $9}' | grep -v '^\.'
gnome-shell --version

```

---

### Post by John Nagle on 2023-05-16
```


$ echo $XDG_SESSION_TYPE
x11
$ ls -l /usr/share/xsessions/ | awk '{print $9}' | grep -v '^\.'

ubuntu.desktop
ubuntu-xorg.desktop
unity.desktop
$ gnome-shell --version
GNOME Shell 42.5

```

---

### Post by #&amp;thj^% on 2023-05-16
please show us this:
```
cat /usr/lib/udev/rules.d/61-gdm.rules
```

---

### Post by MAFoElffen on 2023-05-16
> **John Nagle said:**
> ```


$ echo $XDG_SESSION_TYPE
x11
$ ls -l /usr/share/xsessions/ | awk '{print $9}' | grep -v '^\.'

[COLOR=#ff0000]ubuntu.desktop[/COLOR]
ubuntu-xorg.desktop
unity.desktop
$ gnome-shell --version
GNOME Shell 42.5

```
That is the Ubuntu Desktop with Wayland...

I use and prefer LigntDM, instead of GDM3... And Gnome.
```

mafoelffen@Mikes-ThinkPad-T520:~$  ls -l /usr/share/xsessions/ | awk '{print $9}' | grep -v '^\.'

gnome-classic.desktop
gnome-classic-xorg.desktop
gnome.desktop
gnome-xorg.desktop
ubuntu.desktop
ubuntu-xorg.desktop

```

---

### Post by John Nagle on 2023-05-17
```

$ cat /usr/lib/udev/rules.d/61-gdm.rules
# identify virtio graphics cards to find passthrough setups
SUBSYSTEM!="virtio", GOTO="gdm_virtio_device_end"
ACTION!="add", GOTO="gdm_virtio_device_end"
ATTR{vendor}=="0x1af4", ATTR{device}=="0x0010", RUN+="/usr/bin/touch /run/udev/gdm-machine-has-virtual-gpu", ENV{GDM_MACHINE_HAS_VIRTUAL_GPU}="1", GOTO="gdm_virtio_device_end"
LABEL="gdm_virtio_device_end"

SUBSYSTEM!="pci", GOTO="gdm_pci_device_end"
ACTION!="bind", GOTO="gdm_pci_device_end"

# identify virtio graphics cards to find passthrough setups
# cirrus
ATTR{vendor}=="0x1013", ATTR{device}=="0x00b8", ATTR{subsystem_vendor}=="0x1af4", ATTR{subsystem_device}=="0x1100", RUN+="/usr/bin/touch /run/udev/gdm-machine-has-virtual-gpu", ENV{GDM_MACHINE_HAS_VIRTUAL_GPU}="1", GOTO="gdm_pci_device_end"
# vga
ATTR{vendor}=="0x1b36", ATTR{device}=="0x0100", RUN+="/usr/bin/touch /run/udev/gdm-machine-has-virtual-gpu", ENV{GDM_MACHINE_HAS_VIRTUAL_GPU}="1", GOTO="gdm_pci_device_end"
# qxl
ATTR{vendor}=="0x1234", ATTR{device}=="0x1111", RUN+="/usr/bin/touch /run/udev/gdm-machine-has-virtual-gpu", ENV{GDM_MACHINE_HAS_VIRTUAL_GPU}="1", GOTO="gdm_pci_device_end"

# disable Wayland on Hi1710 chipsets
ATTR{vendor}=="0x19e5", ATTR{device}=="0x1711", GOTO="gdm_disable_wayland"

# disable Wayland on Matrox chipsets
ATTR{vendor}=="0x102b", ATTR{device}=="0x0522", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0524", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0530", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0532", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0533", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0534", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0536", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x102b", ATTR{device}=="0x0538", GOTO="gdm_disable_wayland"

# disable Wayland on aspeed chipsets
ATTR{vendor}=="0x1a03", ATTR{device}=="0x2010", GOTO="gdm_disable_wayland"
ATTR{vendor}=="0x1a03", ATTR{device}=="0x2000", GOTO="gdm_disable_wayland"

LABEL="gdm_pci_device_end"

# disable Wayland if modesetting is disabled
KERNEL!="card[0-9]*", GOTO="gdm_nomodeset_end"
SUBSYSTEM!="drm", GOTO="gdm_nomodeset_end"
IMPORT{parent}="GDM_MACHINE_HAS_VIRTUAL_GPU"
ENV{GDM_MACHINE_HAS_VIRTUAL_GPU}!="1", RUN+="/usr/bin/touch /run/udev/gdm-machine-has-hardware-gpu"
# but keep it enabled for simple framebuffer drivers
DRIVERS=="simple-framebuffer", GOTO="gdm_nomodeset_end"
IMPORT{cmdline}="nomodeset", GOTO="gdm_disable_wayland"
LABEL="gdm_nomodeset_end"

# The vendor nvidia driver has multiple modules that need to be loaded before GDM can make an
# informed choice on which way to proceed, so force GDM to wait until NVidia's modules are
# loaded before starting up.
KERNEL!="nvidia", GOTO="gdm_nvidia_end"
SUBSYSTEM!="module", GOTO="gdm_nvidia_end"
ACTION!="add", GOTO="gdm_nvidia_end"
RUN+="/usr/bin/touch /run/udev/gdm-machine-has-vendor-nvidia-driver"
LABEL="gdm_nvidia_end"

# If this machine has an internal panel, take note, since it's probably a laptop
# FIXME: It could be "ghost connectors" make this pop positive for some workstations
# in the wild. If so, we may have to fallback to looking at the chassis type from
# dmi data or acpi
KERNEL!="card[0-9]-eDP-*", GOTO="gdm_laptop_check_end"
SUBSYSTEM!="drm", GOTO="gdm_laptop_check_end"
ACTION!="add", GOTO="gdm_laptop_check_end"
RUN+="/usr/bin/touch /run/udev/gdm-machine-is-laptop"
GOTO="gdm_hybrid_nvidia_laptop_check"
LABEL="gdm_laptop_check_end"

# If this is a hybrid graphics setup, take note
KERNEL!="card[1-9]*", GOTO="gdm_hybrid_graphics_check_end"
KERNEL=="card[1-9]-*", GOTO="gdm_hybrid_graphics_check_end"
SUBSYSTEM!="drm", GOTO="gdm_hybrid_graphics_check_end"
ACTION!="add", GOTO="gdm_hybrid_graphics_check_end"
RUN+="/usr/bin/touch /run/udev/gdm-machine-has-hybrid-graphics"
LABEL="gdm_hybrid_graphics_check_end"

# If this is a hybrid graphics laptop with vendor nvidia driver, prefer Wayland
LABEL="gdm_hybrid_nvidia_laptop_check"
TEST!="/run/udev/gdm-machine-is-laptop", GOTO="gdm_hybrid_nvidia_laptop_check_end"
TEST!="/run/udev/gdm-machine-has-hybrid-graphics", GOTO="gdm_hybrid_nvidia_laptop_check_end"
TEST!="/run/udev/gdm-machine-has-vendor-nvidia-driver", GOTO="gdm_hybrid_nvidia_laptop_check_end"
GOTO="gdm_end"
LABEL="gdm_hybrid_nvidia_laptop_check_end"

# Disable wayland in situation where we're in a guest with a virtual gpu and host passthrough gpu
LABEL="gdm_virt_passthrough_check"
TEST!="/run/udev/gdm-machine-has-hybrid-graphics", GOTO="gdm_virt_passthrough_check_end"
TEST!="/run/udev/gdm-machine-has-virtual-gpu", GOTO="gdm_virt_passthrough_check_end"
TEST!="/run/udev/gdm-machine-has-hardware-gpu", GOTO="gdm_virt_passthrough_check_end"
GOTO="gdm_disable_wayland"
LABEL="gdm_virt_passthrough_check_end"

# Disable wayland when there are multiple virtual gpus
LABEL="gdm_virt_multi_gpu_check"
TEST!="/run/udev/gdm-machine-has-hybrid-graphics", GOTO="gdm_virt_multi_gpu_check_end"
TEST!="/run/udev/gdm-machine-has-virtual-gpu", GOTO="gdm_virt_multi_gpu_check_end"
TEST=="/run/udev/gdm-machine-has-hardware-gpu", GOTO="gdm_virt_multi_gpu_check_end"
LABEL="gdm_virt_multi_gpu_check_end"

# Disable wayland when nvidia modeset is disabled or when drivers are a lower
# version than 470,
# For versions above 470 but lower than 510 prefer Xorg,
# Above 510, prefer Wayland.
KERNEL!="nvidia_drm", GOTO="gdm_nvidia_drm_end"
SUBSYSTEM!="module", GOTO="gdm_nvidia_drm_end"
ACTION!="add", GOTO="gdm_nvidia_drm_end"
# disable wayland if nvidia-drm modeset is not enabled
ATTR{parameters/modeset}!="Y", GOTO="gdm_disable_wayland"
# disable wayland for nvidia drivers versions lower than 470
ATTR{version}=="4[0-6][0-9].*|[0-3][0-9][0-9].*|[0-9][0-9].*|[0-9].*", GOTO="gdm_disable_wayland"
# For nvidia drivers versions Above 510, prefer Xorg by default
ATTR{version}=="[5-9][1-9][0-9].*", GOTO="gdm_prefer_xorg"
# For nvidia drivers versions 470-495, prefer Xorg by default
GOTO="gdm_prefer_xorg"
LABEL="gdm_nvidia_drm_end"

GOTO="gdm_end"

LABEL="gdm_prefer_xorg"
RUN+="/usr/libexec/gdm-runtime-config set daemon PreferredDisplayServer xorg"
GOTO="gdm_end"

LABEL="gdm_disable_wayland"
RUN+="/usr/libexec/gdm-runtime-config set daemon WaylandEnable false"
GOTO="gdm_end"

LABEL="gdm_end"

```

Lots of very specific NVidia driver version restrictions in there.

---

### Post by John Nagle on 2023-05-17
[https://i.ibb.co/cNHWVht/displaydriver.png](https://i.ibb.co/cNHWVht/displaydriver.png)
And this is the driver in use. 470, the recommended driver, supplied by the Ubuntu distro. 

Looks like "nvidia-drm" is required for Wayland on Nvidia. So, checking syslog:

```

$ grep nvidia-drm syslog
May 14 00:45:51 Nagle-LTS kernel: [   24.035970] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
May 14 00:45:51 Nagle-LTS kernel: [   24.035973] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 0

```
Looks OK.

From the rules, Wayland should be available, but not automatically selected. But I don't even get the option. What am I missing?

---

### Post by MAFoElffen on 2023-05-17
> **John Nagle said:**
> ```

$ cat /usr/lib/udev/rules.d/61-gdm.rules
....
# For nvidia drivers versions 470-495, prefer Xorg by default
GOTO="gdm_prefer_xorg"
LABEL="gdm_nvidia_drm_end"

GOTO="gdm_end"

LABEL="gdm_prefer_xorg"
[COLOR=#ff0000]RUN+="/usr/libexec/gdm-runtime-config set daemon PreferredDisplayServer xorg"[/COLOR]
GOTO="gdm_end"

LABEL="gdm_disable_wayland"
[COLOR=#ff0000]RUN+="/usr/libexec/gdm-runtime-config set daemon WaylandEnable false"[/COLOR]
GOTO="gdm_end"

LABEL="gdm_end"

```

Lots of very specific NVidia driver version restrictions in there.
```

sudo nano /usr/lib/udev/rules.d/61-gdm.rules

```
At the above line (above in red), near the end of the file... 
```

LABEL="gdm_prefer_xorg"
[COLOR=#ff0000]#RUN+="/usr/lib/gdm-runtime-config set daemon PreferredDisplayServer xorg"[/COLOR]
GOTO="gdm_end"

LABEL="gdm_disable_wayland"
[COLOR=#ff0000]#RUN+="/usr/lib/gdm-runtime-config set daemon WaylandEnable false"[/COLOR]
GOTO="gdm_end"

```
Add # to the two lines like what is shown above (scroll all the way down, both are at the bottom, to comment those two lines out. Save, then reboot. At the graphical login, select the gear Icon again, to see if you have the Wayland Option to login from...

Note that is was nVidia themselves, that asked Canonical, right before Ubuntu 22.04's release, to prefer Xorg over Wayland.

---

### Post by #&amp;thj^% on 2023-05-18
> **MAFoElffen said:**
> ```

sudo nano /usr/lib/udev/rules.d/61-gdm.rules

```
At the above line (above in red), near the end of the file... 
```

LABEL="gdm_prefer_xorg"
[COLOR=#ff0000]#RUN+="/usr/lib/gdm-runtime-config set daemon PreferredDisplayServer xorg"[/COLOR]
GOTO="gdm_end"

LABEL="gdm_disable_wayland"
[COLOR=#ff0000]#RUN+="/usr/lib/gdm-runtime-config set daemon WaylandEnable false"[/COLOR]
GOTO="gdm_end"

```
Add # to the two lines like what is shown above (scroll all the way down, both are at the bottom, to comment those two lines out. Save, then reboot. At the graphical login, select the gear Icon again, to see if you have the Wayland Option to login from...

Note that is was nVidia themselves, that asked Canonical, right before Ubuntu 22.04's release, to prefer Xorg over Wayland.
Once again MAFoElffe  thanks for covering in my absence, it's like we are of one mind at times. ;)
If this don't work I have one more suggestion to offer.
To the OP, this may seem/feel like taking a hammer to turn a radio off.....LOL

---

### Post by MAFoElffen on 2023-05-18
> **1fallen said:**
> Once again MAFoElffe  thanks for covering in my absence, it's like we are of one mind at times. ;)
If this don't work I have one more suggestion to offer.
To the OP, this may seem/feel like taking a hammer to turn a radio off.....LOL
LOL. I knew where you were going with that.

Mine works and offers up different options to use Wayland, because I do not use GDM3. I use LightDM as a DM, so mine does not hit the logic in that rule for GDM3. Installing LightDM would be another option.

---

### Post by #&amp;thj^% on 2023-05-18
> **MAFoElffen said:**
> LOL. I knew where you were going with that.

Mine works and offers up different options to use Wayland, because I do not use GDM3. I use LightDM as a DM, so mine does not hit the logic in that rule for GDM3. Installing LightDM would be another option.

Bingo, I'm telling or reporting to the staff you have mind reading powers, scary. :lolflag:
(Clarity Joke)

---

### Post by John Nagle on 2023-05-19
Well, yes, that hack might force Wayland.  Or break something.

But why is Wayland disabled? None of the tests that take control to "gdm_disable_wayland" should be true.

```

# disable Wayland if modesetting is disabled
IMPORT{cmdline}="nomodeset", GOTO="gdm_disable_wayland

```
Not sure about this.

```

# disable wayland if nvidia-drm modeset is not enabled
ATTR{parameters/modeset}!="Y", GOTO="gdm_disable_wayland"

```
Not sure about this.

```

# disable wayland for nvidia drivers versions lower than 470
ATTR{version}=="4[0-6][0-9].*|[0-3][0-9][0-9].*|[0-9][0-9].*|[0-9].*", GOTO="gdm_disable_wayland"

```
Should not take the goto for for driver 470.182.03.

It may be that modesetting is disabled:
```

$ inxi -Gxx
Graphics:
  Device-1: NVIDIA GK107 [GeForce GT 640] vendor: eVga.com. driver: nvidia
    v: 470.182.03 pcie: speed: 2.5 GT/s lanes: 16 bus-ID: 01:00.0
    chip-ID: 10de:0fc1
  Display: x11 server: X.Org v: 1.21.1.4 compositor: gnome-shell v: 42.5
    driver: X: loaded: nvidia unloaded: fbdev,modesetting,nouveau,vesa
    gpu: nvidia display-ID: :1 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 101
  Monitor-1: HDMI-0 res: 1920x1080 dpi: 102 diag: 546mm (21.5")
  OpenGL: renderer: NVIDIA GeForce GT 640/PCIe/SSE2
    v: 4.6.0 NVIDIA 470.182.03 direct render: Yes
$ grep modesetting /var/log/Xorg.0.log
[155004.672] (==) Matched modesetting as autoconfigured driver 2
[155004.802] (II) LoadModule: "modesetting"
[155004.802] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[155004.834] (II) Module modesetting: vendor="X.Org Foundation"
[155004.884] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[155004.901] (WW) Falling back to old probe method for modesetting
[155005.857] (II) UnloadModule: "modesetting"
[155005.857] (II) Unloading modesetting

```

Does that mean modesetting is disabled? And if so, why?

---

### Post by MAFoElffen on 2023-05-19
Do you want to use "Wayland"? If so, then try the change...

As your first post said, my machine has
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep -a1 'Wayland' /etc/gdm3/custom.conf
# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false

```
But my machine does not use GDM3. Yet mine has "Ubuntu on Wayland" offered as a Desktop and starts Wayland through LightDM. 

You could keep asking "Why?"... Or you could try it and see if it works. That is your choice. 

You don't have to do anything you do not want to. Nor do I "need" to recommend more. Right? I am here to help people who want and need help.

I am not in any way connected with Canonical, nor is any else here. We are all just volunteers helping each other. I cannot say why Canonical does things. I can only look at what is there, test what does and doesn't work.  We are given what is there to work with, and to try to make the best of it. Given the way it is presented to us, the "Why" is not important, as we cannot change their reasons behind those. We can only change what "we have."

Does that make sense to you? Just trying to help you.

---

### Post by John Nagle on 2023-05-19
Turns out this is a known Ubuntu bug: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1968929](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1968929)

It was supposedly fixed, but comments after the fix indicate it is still broken, at least in LTS releases.

---

### Post by MAFoElffen on 2023-05-19
You responded to a closed bug report, without opening a new bug (?) and referred back to this thread.

...and yet (in this thread), you still didn't try *anything* we suggested. LOL. They can now see your *commitment*. I can see this is not going to get anywhere. Oh, well. On to other things.

+1 = Do as they asked you to do: File a new bug report.

If that is what you would like to pursue.. I hope you follow their instructions and try the things they suggest.

Hopefully you will commit to your own participation in your solution. People cannot do that for you. 

Just with trying to help you here-- You did not do so "here." When we asked you for information by posting output to commands, you fought it and resisted. When asked to try things, and see if it worked, you just didn't. We can't force you to participate. And you would have to pay me lots to do it for you, without you involved in the solution. (I am an IT Consultant.) And "Not all money is good money."

I hope you will post back here with updates on your progress.

Sincerely and honestly-- I wish you well.

---

### Post by John Nagle on 2023-05-20
OK. Created new bug report, with all the details: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/2020249](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/2020249)

Commenting out all those tests for not using Wayland is the big-hammer approach. I'd expect that to have side effects. Ones not reportable as bugs, since checks had been bypassed.
So that's not a permanent solution.

Wayland vs. NVidia has been a problem since 2019, and has been "fixed" several times. The problem still keeps coming up in some configurations.

---

