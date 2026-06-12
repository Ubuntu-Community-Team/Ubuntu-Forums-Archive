---
title: "SN9C10x webcam not working with zoneminder 1.22.3"
date: 2007-05-27
forum: General Help
---

### Post by blankko on 2007-05-27
I'm trying to use my SN9C10x webcam with zoneminder. I've installed zoneminder successfully and tried to add /dev/video0 to zoneminder but zoneminder doesn't seem to be getting the video stream from my webcam.

I've then installed mplayer and xawtv to test my webcam video output. I failed to get video on both applications from my webcam.

I later ran 'apt-get install webcam' because I read on the forums that it might help. However the I still cannot get video output from either mplayer, xawtv or zoneminder.
The following are my dmesg and application output message. Does anyone know where the problem lies?

_dmesg output:_

Linux video capture interface: v2.00
sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.27
usb 1-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x6025)
usb 1-1: TAS5130D1B image sensor detected
usb 1-1: Initialization succeeded
usb 1-1: V4L2 device registered as /dev/video0
usbcore: registered new interface driver sn9c102


_v4l-conf message:_

faber@faber-xubuntu:/dev$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=5120, base=0xd2000000
/dev/video0 [v4l2]: no overlay support
faber@faber-xubuntu:/dev$


_xawtv -hwscan results:_

faber@faber-xubuntu:/dev$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
looking for available devices
port 65-96
    type : Xvideo, image scaler
    name : NV Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : SN9C10x PC Camera
    flags:  capture  

faber@faber-xubuntu:/dev$ 


_xawtv messages:_

faber@faber-xubuntu:/dev$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb7ddb990b7f78e52 [PAL_B1,PAL_I,PAL_D1,PAL_N,PAL_Nc,PAL_60,?,SECAM_B,SECAM_D,SECAM_G,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
no way to get: 384x288 32 bit TrueColor (LE: bgr-)
no way to get: 384x288 32 bit TrueColor (LE: bgr-)
no way to get: 384x288 32 bit TrueColor (LE: bgr-)
faber@faber-xubuntu:/dev$ 


_Mplayer error message:_

faber@faber-xubuntu:/dev$ mplayer tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: SN9C10x PC Camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = Camera;
 Current input: 0
 Current format: unknown (0x31384142)
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
faber@faber-xubuntu:/dev$

---

### Post by jwasys on 2007-05-29
I get  literally the same results. Ubuntu 7.0.4. Someone ?

dmesg:
[545579.980595] usb 1-4: new full speed USB device using ohci_hcd and address 9
[545580.190028] usb 1-4: configuration #1 chosen from 1 choice
[545580.195893] usb 1-4: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x6005)
[545580.357853] usb 1-4: TAS5110C1B image sensor detected
[545580.435794] usb 1-4: Initialization succeeded
[545580.435847] usb 1-4: V4L2 device registered as /dev/video0

Arian

---

### Post by nab on 2007-10-20
Hallo,

here the same on Ubuntu 7.04

dmesg:

```

[  124.032000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  124.192000] usb 3-1: configuration #1 chosen from 1 choice
[  124.400000] Linux video capture interface: v2.00
[  124.452000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.27
[  124.452000] usb 3-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x6028)
[  124.492000] usb 3-1: PAS202BCB image sensor detected
[  125.008000] usb 3-1: Initialization succeeded
[  125.008000] usb 3-1: V4L2 device registered as /dev/video0
[  125.008000] usbcore: registered new interface driver sn9c102
[  125.096000] usbcore: registered new interface driver gspca
[  125.096000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

```

In GStreamer Properties the webcam is found. But on testing I get the error message:
Video for Linux 2 (v4l2): Could not negotiate format

In Ekiga the webcam works.

Any suggestion?
TIA
Niko

---

### Post by nab on 2007-10-20
Well,...

Remembering that my webcam did work under earlier version of ubuntu I got my webcam working with v4l instead of v4l2:

I added as root in /etc/modprobe.d/blacklist following line:

blacklist sn9c102

To prevent the modul sn9c102 from loading. A look in the system log shows the webcam uses the modul gspca now.

Ok I'm not satisfied with result (color blueish, only 320x280), but it is working again.

Hope this trick works for you too.
Niko

---

### Post by jbaloul on 2007-11-16
Thanks Niko, worked perfectly...got it to work with Skype 2.0 beta as well...
here are the steps:
unplug camera
sudo vim  /etc/modprobe.d/blacklist
	add:
```

	#webcam bad driver
	blacklist sn9c102

```

sudo apt-get install gspca-source build-essential linux-headers-`uname -r`
cd /usr/src
sudo tar -xjf gspca-source.tar.bz2
cd modules/gspca/
sudo ./gspca_build
sudo depmod -a
plug in camera

you should see this in /var/log/messages :
/usr/src/modules/gspca/gspca_core.c: USB GSPCA camera found. SONIX sn9c10[1 2]

like a glove,
Jacob
[http://howtoforums.net](http://howtoforums.net)

Edit: i did this in gutsy, and you mite have to add this to /etc/apt/sources.list and run sudo apt-get update
```

#webcam drivers
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

```

---

### Post by lptr on 2008-01-21
Forgive my jumping in:
V4L2 supporting here real high quality video streams from Phillips SPC900NC webcam out of the box. 

Anyone knowing if zoneminder will be using V4L2 instead of V4L in near future?

rob*

---

### Post by vivalant on 2008-01-21
Try the Generic SN9CXXX driver  at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by lcastillo on 2008-03-30
I have the same problem. I force this camera to work with the V4L, and it works with xawtv, but with zoneminder i can get an image, and the logs said "shared memory not valid" but i have a 1 Gb RAM.

help me please :(

---

### Post by lptr on 2008-03-31
Did you try this?
```
# /etc/sysctl.conf - Configuration file for setting system variables
# Shared memory settings changed for ZoneMinder (ZM)
kernel.shmall = 134217728 (=128MB)
kernel.shmmax = 134217728

To determine current shared memory limits 
roberts@kulix:~$ ipcs -lm
------ Shared Memory Limits --------
max number of segments = 4096
max seg size (kbytes) = 32768
max total shared memory (kbytes) = 8388608
min seg size (bytes) = 1
```rob*

btw: There was no reason to change away from V4L2, at least for SPC900NC

---

