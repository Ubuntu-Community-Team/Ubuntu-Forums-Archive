---
title: "Dual monitor and random sleep like behavior"
date: 2013-03-20
forum: General Help
---

### Post by nef131 on 2013-03-20
I am running Ubuntu 21.04 but have installed and am using KDE as my desktop environment. I tried to set up to use an HD TV as a second monitor so that I could watch a movie. In a nutshell, both monitors would randomly go black (about once a minute or so) together and the video I was watching would  stop, as if the computer had gone to sleep. However, any button (not  just the on/off switch) would quickly awaken both monitors - with the  laptop's monitor waking up about a second earlier than the TV - and the video would resume from the  point the screen went black. The TV would miss the first second of video on this wakeup because video would resume when the laptop monitor became active.

I set up the TV as a monitor using an HDMI cable. The TV was set up to be a full clone of the laptop's display, with the output set to be unified (i.e., the output to each monitor had the same resolution, etc., so that each display appeared to be identical). I used the KDE program Size and Orientation in System Settings, which seemed to work ok. It did, however, mess up the panel but, I assume, that has nothing to do with the problem in issue.

 The problem occured for the first time when I ran a video program via a browser (in this case netflix, which uses a wine version of firefox but, please note, the same thing happened when I attempted to use vmware player to run windows as a guest OS, although I never did start up netflix). I have not kept the TV connected to the laptop so, at this point, I do not know if the problem also occurs at random points when I am not actively running the computer. I suspect that it does.  In any event, both monitors would go black together (and about once each minute) and the video I was watching would stop, as if the computer had gone to sleep. However, any button (not just the on/off switch) would quickly awaken both monitors - with the laptop's monitor waking up first - and the video would resume from the point the screen went black.

Please note that I set the power saver controls so that the screen was not supposed to turn off. Moreover, when the power saver control is, in fact, set to turn the monitor off when no input has occured for a length of time, it is not set to turn off the screen in a minute or anything of the sort.

My computer is a Dell 15R (N4050) laptop with an Intel I3 processor and with an Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller]). The output of lshw for the display is as follows:

> *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:fb000000-fb3fffff memory:c0000000-cfffffff ioport:f080(size=8)


Further information abouit the graphics from the System Profile and Benchmark program is as follows:
> -Display-
Resolution        : 1366x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.11.3
-Monitors-
Monitor 0        : 1366x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor        : Tungsten Graphics, Inc
Renderer        : Mesa DRI Intel(R) Ironlake Mobile 
Version        : 2.1 Mesa 8.0.4
Direct Rendering        : Yes


I hope that there is a way to do things without having to sit and "wake" up the computer every minute or so.

---

