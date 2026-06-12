---
title: "How to perfectly set up nvidia GTX 860M graphic card?"
date: 2015-04-20
forum: General Help
---

### Post by sebastiaan5 on 2015-04-20
Lenovo y50-70  , intel core i7-4710HQ CPU 2.50ghz * 8 , 64bit  ,  Ubuntu 14.04.02 LTS


First of all I don't want to upgrade my linux for super good ultra gaming, I want to set my driver/everything right for my graphic card so I don't get any trouble with it. I do like to game sometimes, and want to do this on Ubuntu however some small games like: Left4Dead2, minecraft, and maybe some other steam linux games (no games via Wine). 

I have installed a lot of packages and set up my graphic card I think pretty decent because all games are running very smoothly (fe. Minecraft 1600fps+).

Recently I had a graphic card crash while running a game (doesn't occur any more, did sudo apt-get autoremove and doesn't crash any more (I hope)).

I post this thread to have some feedback if I installed the right packages, what I did wrong or what to change.


How I run my driver:

application: 

NVIDIA X SERVER SETTINGS

packages installed to run it (all with synaptic package manager):

bbswitch-dkms
libcuda1-331
libvdpau1
nvidia-331
nvidia-libopencl1-331
nvidia-opencl-icd-331
nvidia-prime
nvidia-settings
ubuntu-drivers-common
xserver-xord-video-nouveau-lts-utopic

In the NVIDIA X server Settings:

Nvidia Driver Version 331.113.
I left everything default except I set the PRIME PROFILES instead of intel I clicked NVIDIA
Total Dedicated Memory: 4096MB
VBIOS Version 82.07.34.00.08
no antialiasing settings enabled (just Use Application Settings on, rest is off).
PowerMizer's current Mode is on Adaptive.
I have no Application profiles
As I see it my gtx 860m is always running, is this true? and is this bad?


My .nvidia.settings-rc text file:

```

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Memory_Used_(GPU_0),Yes,3000

# Attributes:

0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/TextureClamping=1
0/FXAA=0
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0

```


This is a very long thread, I'm sorry :/ and I think most of the information I post is I think not very useful. If you need more information you may always ask :)




greetings

---

### Post by sebastiaan5 on 2015-04-21
bump

---

### Post by sebastiaan5 on 2015-04-21
I still get PC crashes :/ while doing anything intensive for my graphic card :/

---

### Post by buzzingrobot on 2015-04-21
You can visit nvidia.com to determine if the 331 driver is the appropriate driver for the 860M.

The most reliable way to install proprietary drivers on Ubuntu is via the Additional Drivers tool.  That's also the most reliable way to remove a proprietary driver. (You really need to cleanly remove all the components of a broken driver install before trying another one.)

If you're satisfied with the performance of the open source Nouveau driver, use it and skip all the proprietary hassles.

---

