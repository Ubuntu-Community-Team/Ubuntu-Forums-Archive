---
title: "Laptop camera not working -- black screen and flickering"
date: 2023-11-09
forum: General Help
---

### Post by Atirag on 2023-11-09
[COLOR=#0C0D0E][FONT=-apple-system]My Laptop camera is not working and I'm not sure what to do. The screen on Cheese is black and sometimes flickering, the light next to the camera turns on so I know it detects and turns it on. Here is some info.

I also disabled secureboot

[/FONT][/COLOR]```
uname -a
Linux odrec 6.2.0-36-generic #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct  9 15:34:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

guvcview 
GUVCVIEW: version 2.0.7 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
V4L2_CORE: (UVCIOC_CTRL_MAP) Error: No such file or directory 
ALSA lib pcm_dmix.c:1032:(snd_pcm_dmix_open) unable to open slave 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side 
ALSA lib pcm_route.c:877:(find_matching_chmap) Found no matching channel map 
Cannot connect to server socket err = No such file or directory 
Cannot connect to server request channel 
jack server is not running or cannot be started 
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock 
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock 
Cannot connect to server socket err = No such file or directory 
Cannot connect to server request channel 
jack server is not running or cannot be started 
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock 
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock 
ALSA lib pcm_oss.c:397:(_snd_pcm_oss_open) Cannot open device /dev/dsp 
ALSA lib pcm_oss.c:397:(_snd_pcm_oss_open) Cannot open device /dev/dsp 
ALSA lib confmisc.c:160:(snd_config_get_card) Invalid field card 
ALSA lib pcm_usb_stream.c:482:(_snd_pcm_usb_stream_open) Invalid card 'card' 
ALSA lib confmisc.c:160:(snd_config_get_card) Invalid field card 
ALSA lib pcm_usb_stream.c:482:(_snd_pcm_usb_stream_open) Invalid card 'card' 
ALSA lib pcm_dmix.c:1032:(snd_pcm_dmix_open) unable to open slave 
Cannot connect to server socket err = No such file or directory 
Cannot connect to server request channel 
jack server is not running or cannot be started 
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock 
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock 
control[0]:(unknown - 0x6) 0x980001 'User Controls' 
control[12]:(unknown - 0x6) 0x9a0001 'Camera Controls'


v4l2-ctl --list-devices -D
Integrated_Webcam_FHD: Integrat (usb-0000:00:14.0-3):
    /dev/video0
    /dev/video1
    /dev/video2
    /dev/video3
    /dev/media0
    /dev/media1

Driver Info:
    Driver name      : uvcvideo
    Card type        : Integrated_Webcam_FHD: Integrat
    Bus info         : usb-0000:00:14.0-3
    Driver version   : 6.2.16
    Capabilities     : 0x84a00001
        Video Capture
        Metadata Capture
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps      : 0x04200001
        Video Capture
        Streaming
        Extended Pix Format
Media Driver Info:
    Driver name      : uvcvideo
    Model            : Integrated_Webcam_FHD: Integrat
    Serial           : 
    Bus info         : usb-0000:00:14.0-3
    Media version    : 6.2.16
    Hardware revision: 0x00001491 (5265)
    Driver version   : 6.2.16
Interface Info:
    ID               : 0x03000002
    Type             : V4L Video
Entity Info:
    ID               : 0x00000001 (1)
    Name             : Integrated_Webcam_FHD: Integrat
    Function         : V4L2 I/O
    Flags            : default
    Pad 0x01000007   : 0: Sink
      Link 0x02000013: from remote pad 0x100000a of entity 'Extension 4' (Video Pixel Formatter): Data, Enabled, Immutable

ls -al /dev/video*
crw-rw----+ 1 root video 81, 0 Nov  9 01:40 /dev/video0
crw-rw----+ 1 root video 81, 1 Nov  9 01:40 /dev/video1
crw-rw----+ 1 root video 81, 2 Nov  9 01:40 /dev/video2
crw-rw----+ 1 root video 81, 3 Nov  9 01:40 /dev/video3

lshw -c video
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: GA103M [GeForce RTX 3080 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: iomemory:600-5ff iomemory:640-63f irq:214 memory:96000000-96ffffff memory:6000000000-63ffffffff memory:6400000000-6401ffffff ioport:3000(size=128) memory:97080000-970fffff
  *-display
       description: VGA compatible controller
       product: Alder Lake-HX GT1 [UHD Graphics 770]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=3840,2160
       resources: iomemory:640-63f iomemory:400-3ff irq:213 memory:645e000000-645effffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff
```

---

### Post by yancek on 2023-11-09
Do you have video for linux (V4L) installed?  Note several errors in your output referring to V4L with no such file or director.  The link below explains how to install so try that first and post back the results.  You haven't indicated which version of Ubuntu you are using?

[https://installati.one/install-v4l-utils-ubuntu-20-04/](https://installati.one/install-v4l-utils-ubuntu-20-04/)

---

### Post by Atirag on 2023-11-14
I posted the ubuntu version above


[COLOR=#000000][FONT=&amp]uname -aLinux odrec 6.2.0-36-generic #37~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Oct  9 15:34:04 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

[/FONT][/COLOR]and i checked and I have V4L already installed
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by SeijiSensei on 2023-11-14
My Dell laptop came with a shutter over the camera. Drove me crazy when cheese always showed a black screen. Discovered the shutter, opened it, and now everything works as expected.

---

### Post by Atirag on 2023-11-20
Hahahaha no way. That was the issue. The shutter switch was a bit hidden and it's a computer I grabbed from work so I didn't know it had that. Thanks a lot.

---

### Post by yancek on 2023-11-20
>  I posted the ubuntu version above

No, what you posted was the kernel you are using which gives an idea but not the actual Ubuntu release version.  You can get that from a terminal with the command below:

```
cat /etc/issue
```

Since you got it working with the suggestion given, not a problem but useful info for future use.

---

### Post by Atirag on 2023-11-20
Ah I see, thanks!

---

