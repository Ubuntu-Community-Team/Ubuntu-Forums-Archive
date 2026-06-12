---
title: "Which driver to install for Nvidia GT8500 card"
date: 2013-02-24
forum: General Help
---

### Post by DeMus on 2013-02-24
Hi,

My computer with a Q6600 quadcore processor, 4GB ram and 2 500GB disks has a nVidia GT8500 graphics card. The processor is not running at 2.GHz but at 3GHz, giving it a 25% boost.
Still, when watching videos, the image sometimes freezes. I think this might be caused by a faulty graphics driver or wrong setting.
In the attachment you see what I installed to get the card working. Is there something wrong, missing or installed too much?

In the file .nvida-settings-rc I see this:

#
# /home/jan/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sat Feb 9 14:38:03 2013
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = No
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Memory_Used_(GPU_0),Yes,3000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=1
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/TextureClamping=1
0/FXAA=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/DigitalVibrance[DFP-0]=0
0/ColorSpace[DFP-0]=0
0/ColorRange[DFP-0]=0
0/XVideoSyncToDisplay=65536


Who can help me with this? Which drivers do you guys install to make it run smoothly?

Thanks.

---

### Post by bogan on 2013-02-24
Hi!, **DeMus**,

Exactly which driver version is in use at present?
Please Post:```
uname -r 
lspci -nnk | grep -iA3 vga 
/usr/lib/nux/unity_support_test -p
apt-cache policy nvidia-current-updates

```Have you run 'nvidia-settings? or NVIDIA X Server Settings, and if so, does it show the nvidia driver in use?

Chao!, **bogan**.

---

### Post by DeMus on 2013-02-24
Hi Bogan,

thank for responding to my question.
I did what you asked me to do, except for the 3rd line. I use Kubuntu and apparently don't have the Unity support.

**uname -r**
3.5.0-25-generic

**lspci -nnk | grep -iA3 vga**
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86 [GeForce 8500 GT] [10de:0421] (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device [1043:824e]
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb

**apt-cache policy nvidia-current-updates**
nvidia-current-updates:
  Installed: [COLOR="Red"](none)[/COLOR]
  Candidate: 304.51-0ubuntu1
  Version table:
     304.51-0ubuntu1 0
        500 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status

Since I, in the mean time, uninstalled the nvidia-current-updates it says here Installed: none
I did install the nvidia-current and that gives me this:

**apt-cache policy nvidia-current**
nvidia-current:
  Installed: 304.64-0ubuntu1~quantal~xup1
  Candidate: 304.64-0ubuntu1~quantal~xup1
  Version table:
 *** 304.64-0ubuntu1~quantal~xup1 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     304.51.really.304.43-0ubuntu1 0
        500 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages

Same problem. Picture freezes sometimes.

From the list of nvidia, noeveau and vdpau I see in the package manager, which do I need to install and which not? The ones I have installed right now, see picture in original post, do they work together, or do they block each other, or do some do nothing?
What should I do to make it work?

Thanks again.

---

### Post by bogan on 2013-02-24
Hi!, **DeMus**,

You Posted:> From the list of nvidia, noeveau and vdpau I see in the package manager,  which do I need to install and which not? The ones I have installed  right now, see picture in original post, do they work together, or do  they block each other, or do some do nothing?They are all OK as they are and will not block each other, with the possible exception of the need to blacklist nouveau, which is installed by default with the kernal.

As you have uninstalled nvidia-current-updates - or, at least I assume you have - and installed nvidia-current, it is possible that you need nvidia-settings rather than nvidia-settings-updates, but I doubt there is any critical difference.> Have you run 'nvidia-settings? or NVIDIA X Server Settings, and if so, does it show the nvidia driver in use?Unstead of: 'unity_support-test' you could try:```
glxinfo| grep -i openGL
```AS to: "What should I do to make it work?",   I am not familiar with the differences between Ubuntu and Kubuntu and do not know what else to suggest, unless the answer to those last two queries reveal a fault.

 Chao!, **bogan**.

---

### Post by DeMus on 2013-02-24
When I use nvidia-settings I do see the driver which is in use: 304.64
I did change 2 settings in this program to have a bit less quality and some more speed, but I wonder it this will help.

```
glxinfo| grep -i openGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8500 GT/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 304.64
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
```

Thanks again, Bogan.

---

