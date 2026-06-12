---
title: "How to start an aplication and have it use the NVidia graphic card ?"
date: 2023-02-07
forum: General Help
---

### Post by georgesgiralt on 2023-02-07
Hi !
My laptop, running Ubuntu 20.04.5 LTS software has an Intel processor with a graphic card in it which is used by default. It is also fitted with an NVidia MX450 graphic card. 
I can start an app, say VLC, ant this app will use the Intel default graphic card. Fine. 
I can also use the right mouse button to open a menu when I point to the VLC icon on my favourites pane and select to start the application to use the NVidia card. 
Question : how do I proceed to launch VLC from a bash shell and make it use the NVidia card instead of the default Intel graphic card ? A long time ago I used ```
 $ prime vlc 
``` but this prime command is gone....

---

### Post by #&amp;thj^% on 2023-02-07
This is a good detailed read for you: [https://ubuntuhandbook.org/index.php/2021/06/install-nvidia-driver-switch-between-intel-nvidia-ubuntu/](https://ubuntuhandbook.org/index.php/2021/06/install-nvidia-driver-switch-between-intel-nvidia-ubuntu/)
Start around the line>>Run certain apps via NVIDIA GPU while rendering desktop via integrated graphics
Hopefully that  should work for your use.
```
prime-select -q
Usage: /usr/bin/prime-select nvidia|intel|on-demand|query

```
My example I'll use this for kodi:
```
kodi __GLX_VENDOR_LIBRARY_NAME=nvidia

```

---

### Post by georgesgiralt on 2023-02-08
Hello 1fallen,
Thank you very much for your answer. 
I've to read the Ubuntu Handbok (I did'nt know it existed) 
but your solution does not work : 
```

$ vlc __GLX_VENDOR_LIBRARY_NAME=nvidia
VLC media player 3.0.9.2 Vetinari (revision 3.0.9.2-0-gd4c1aefe4d)
[00005649366ce5b0] main libvlc: Lancement de vlc avec l'interface par défaut. Utiliser «*cvlc*» pour démarrer VLC sans interface.
[00007f4460001660] filesystem stream error: cannot open file /home/georges/__GLX_VENDOR_LIBRARY_NAME=nvidia (No such file or directory)
QObject::~QObject: Timers cannot be stopped from another thread
$ 
```
And VLC tells me that he can't open __GLX_VENDOR_LIBRARY_NAME=nvidia as a video or sound stream .....

---

### Post by monkeybrain20122 on 2023-02-08
> **georgesgiralt said:**
> Hello 1fallen,
Thank you very much for your answer. 
I've to read the Ubuntu Handbok (I did'nt know it existed) 
but your solution does not work : 
```

$ vlc __GLX_VENDOR_LIBRARY_NAME=nvidia
VLC media player 3.0.9.2 Vetinari (revision 3.0.9.2-0-gd4c1aefe4d)
[00005649366ce5b0] main libvlc: Lancement de vlc avec l'interface par défaut. Utiliser «*cvlc*» pour démarrer VLC sans interface.
[00007f4460001660] filesystem stream error: cannot open file /home/georges/__GLX_VENDOR_LIBRARY_NAME=nvidia (No such file or directory)
QObject::~QObject: Timers cannot be stopped from another thread
$ 
```
And VLC tells me that he can't open __GLX_VENDOR_LIBRARY_NAME=nvidia as a video or sound stream .....

Shouldn't it be 
 
 ```
__GLX_VENDOR_LIBRARY_NAME=nvidia vlc

``` ?

By putting vlc in front vlc is trying to open whatever after, in this case obvious it doesn't exist.

---

### Post by georgesgiralt on 2023-02-08
Tried it but no joy. 
```
$ __GLX_VENDOR_LIBRARY_NAME=nvidia vlc
VLC media player 3.0.9.2 Vetinari (revision 3.0.9.2-0-gd4c1aefe4d)
[0000564c6b2b05b0] main libvlc: Lancement de vlc avec l'interface par défaut. Utiliser «*cvlc*» pour démarrer VLC sans interface.
[0000564c6b33da00] main playlist: playlist is empty
[00007fbfb0c13c60] main demux error: option sub-original-fps does not exist
[vobsub @ 0x7fbfb186f9c0] Unable to open /freebox/disque/Enregistrements/France 2 - Rugby Tournoi des Six Nations (Tournoi des Six Nations 2023 1re journée - Italie France) - 05-02-2023 15h50 02h55 (58).m2ts.sub as MPEG subtitles
[00007fbfb0c13c60] avformat demux error: Could not open /freebox/disque/Enregistrements/France 2 - Rugby Tournoi des Six Nations (Tournoi des Six Nations 2023 1re journée - Italie France) - 05-02-2023 15h50 02h55 (58).m2ts.idx: No such file or directory
[00007fbfc810a080] main input error: demux doesn't like DEMUX_GET_TIME
[00007fbfc810a080] main input error: demux doesn't like DEMUX_GET_TIME
[00007fbfc810a080] main input error: slave[0] doesn't like DEMUX_GET_TIME -> EOF
[00007fbfb194f240] mpeg4audio packetizer: AAC channels: 2 samplerate: 24000
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
[00007fbfb186a5a0] avcodec decoder: Using Intel iHD driver for Intel(R) Gen Graphics - 20.1.1 () for hardware decoding

```
I've tried to change the .desktop file as per the Ubuntu Handbook but I bet I need to log out/in for it to work... 
So I wonder if the old "prime" command was a true blessing ;-)

---

### Post by #&amp;thj^% on 2023-02-08
> So I wonder if the old "prime" command was a true blessing 
It was indeed. :d
> I've tried to change the .desktop file as per the Ubuntu Handbook but I bet I need to log out/in for it to work... 
I have not had to touch any of those .desktop file on XFCE
See screenshots and commands *I've used:
Also can I see this please 
```
sudo prime-select query
**_on-demand_**


```
Also I have a hybrid set-up AMD and Nvidia, but for the most part I run the Nvidia card as default.
```
inxi -G | grep nvidia
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
  Display: x11 server: X.Org v: 1.21.1.6 driver: X: loaded: nvidia
    gpu: nvidia,nvidia-nvswitch resolution: 1: 1920x1080~120Hz 2: N/A


```
Also there is more tweaks i can offer but I'm afraid that what works for me won't work for you..
EDIT: wouldn't hurt to see this as well:
```
me on Wed Feb 08 at 10:28 AM in ~ branch: (HEAD) 
>>[COLOR="#FF0000"]  lsmod | grep nouveau
[/COLOR]

me on Wed Feb 08 at 10:41 AM in ~ branch: (HEAD) 
>>[COLOR="#FF0000"] lsmod | grep nvidia[/COLOR]
nvidia_uvm           1396736  0
nvidia_drm             69632  3
nvidia_modeset       1212416  6 nvidia_drm
nvidia              56356864  261 nvidia_uvm,nvidia_modeset
drm_kms_helper        200704  1 nvidia_drm
drm                   585728  7 drm_kms_helper,nvidia,nvidia_drm


```

---

### Post by georgesgiralt on 2023-02-08
Thank you for your answer. 
I've written a Bash shell script positioning the correct environment variables and then run the command given as an arg. seems to work fine. 
Guess what is it's name ? Prime, of course ! ;-)
As per running all my graphics on the NVidia chip is a no go as this drains the battery fast. And I do not need it that often and not for a lot of apps. 
So for me, problem solved for now. 
Thanks for your help and making me discover the Ubuntu Handbook which is quite good.
Edit : My script does not work. See : 
```
$ Prime vlc
VLC media player 3.0.9.2 Vetinari (revision 3.0.9.2-0-gd4c1aefe4d)
[000055677b2c65b0] main libvlc: Lancement de vlc avec l'interface par défaut. Utiliser «*cvlc*» pour démarrer VLC sans interface.
[000055677b353a00] main playlist: playlist is empty
[00007f124cc13100] main demux error: option sub-original-fps does not exist
[vobsub @ 0x7f124d86eb80] Unable to open /freebox/disque/Enregistrements/TF1 - Rugby Coupe du monde féminine (Coupe du monde féminine 2022 Match pour la 3e place - Canada France) - 12-11-2022 04h20 02h10 (40).m2ts.sub as MPEG subtitles
[00007f124cc13100] avformat demux error: Could not open /freebox/disque/Enregistrements/TF1 - Rugby Coupe du monde féminine (Coupe du monde féminine 2022 Match pour la 3e place - Canada France) - 12-11-2022 04h20 02h10 (40).m2ts.idx: No such file or directory
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: demux doesn't like DEMUX_GET_TIME
[00007f1260000990] main input error: slave[0] doesn't like DEMUX_GET_TIME -> EOF
[00007f124d94ba60] mpeg4audio packetizer: AAC channels: 2 samplerate: 48000
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
[00007f124d83b4a0] avcodec decoder: Using Intel iHD driver for Intel(R) Gen Graphics - 20.1.1 () for hardware decoding
[h264 @ 0x7f1254075000] get_buffer() failed
[h264 @ 0x7f1254075000] thread_get_buffer() failed
[h264 @ 0x7f1254075000] decode_slice_header error
[h264 @ 0x7f1254075000] no frame!
[h264 @ 0x7f12540913c0] get_buffer() failed
[h264 @ 0x7f12540913c0] thread_get_buffer() failed
[h264 @ 0x7f12540913c0] decode_slice_header error
[h264 @ 0x7f12540913c0] no frame!
QObject::~QObject: Timers cannot be stopped from another thread
$
```
See the line : ```
[00007f124d83b4a0] avcodec decoder: Using Intel iHD driver for Intel(R) Gen Graphics - 20.1.1 () for hardware decoding
```

Your example does not say anything about the graphics card being used because you have to open a media for the graphics device to be used. 
I forgot to add that there is no nouveau modules loaded as they make my laptop a brick and that I have a bunch of NVidia modules loaded.

---

### Post by #&amp;thj^% on 2023-02-08
I'm not a VLC fan I used to be but snot no more...lol
```
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia vlc
VLC media player 3.0.18 Vetinari (revision 3.0.13-8-g41878ff4f2)
[0000559e557505d0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0000559e557e6b00] main playlist: playlist is empty
[0000559e55822cf0] main audio output error: too low audio sample frequency (0)
[00007f4d1cda7bd0] main decoder error: failed to create audio output
[0000559e55822cf0] vlcpulse audio output error: digital pass-through stream connection failure: Input/Output error
[0000559e55822cf0] main audio output error: module not functional
[00007f4d1cda7bd0] main decoder error: failed to create audio output
libEGL warning: DRI3: Screen seems not DRI3 capable
libEGL warning: DRI2: failed to authenticate
[00007f4d00004350] gl gl: Initialized libplacebo v4.208.0 (API v208)
libEGL warning: DRI3: Screen seems not DRI3 capable
libEGL warning: DRI2: failed to authenticate
[00007f4d00004350] gl gl: Initialized libplacebo v4.208.0 (API v208)


```
I'm still looking into this:
What nvidia-driver version are you now using?

---

### Post by #&amp;thj^% on 2023-02-08
I've been playing with "~/config/vlc/vlrc"
this has been working ok on my end:
```

# Lua interface configuration (string)
lua-config= __NV_PRIME_RENDER_OFFLOAD_PROVIDER=NVIDIA-G0 __GLX_VENDOR_LIBRARY_NAME=nvidia
```
Then it just opens as 
```
vlc
```
I just don't on my end see it using my AMD gpu...
EDIT: Gosh I keep forgetting about snaps, this is my view on that>>> out of site out of mind. (Sorry)
This isn't a snap vlc is it?

---

### Post by georgesgiralt on 2023-02-08
Hi
I use : ```
nvidia-driver-470                             470.161.03-0ubuntu0.20.04.1                 amd64        NVIDIA driver metapackage
```
I did not thought about 
~/config/vlc/vlrc
And the relevant .config file for other apps I plan to use with NVidia GPU.... 
I'm getting too old ! 
As per snap apps, on this laptop, I'm proud of not using any.... But things will have to change when I'll configure the Ubuntu Pro or switch to the next Ubuntu version.... 
IMHO it is the wrong way to solve problems, introducing new one without solving the initial problems... But it's just an old guy ranting....

---

### Post by #&amp;thj^% on 2023-02-09
I thought so on the 470 driver, i hope everything is working to your satisfaction, but here is enough diffs between yours and mine, as in:
```
apt list --installed '*nvidia*'
Listing... Done
libnvidia-cfg1-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-common-525/lunar,lunar,now 525.78.01-0ubuntu1 all [installed,automatic]
libnvidia-compute-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-compute-525/lunar,now 525.78.01-0ubuntu1 i386 [installed,automatic]
libnvidia-decode-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-decode-525/lunar,now 525.78.01-0ubuntu1 i386 [installed,automatic]
libnvidia-egl-wayland1/lunar,now 1:1.1.10-1 amd64 [installed,automatic]
libnvidia-encode-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-encode-525/lunar,now 525.78.01-0ubuntu1 i386 [installed,automatic]
libnvidia-extra-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-fbc1-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-fbc1-525/lunar,now 525.78.01-0ubuntu1 i386 [installed,automatic]
libnvidia-gl-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
libnvidia-gl-525/lunar,now 525.78.01-0ubuntu1 i386 [installed,automatic]
nvidia-compute-utils-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
nvidia-dkms-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
nvidia-driver-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed]
nvidia-kernel-common-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
nvidia-kernel-source-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
nvidia-prime/lunar,lunar,now 0.8.17.1 all [installed,automatic]
nvidia-settings/lunar,now 510.47.03-0ubuntu1 amd64 [installed,automatic]
nvidia-utils-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-525/lunar,now 525.78.01-0ubuntu1 amd64 [installed,automatic]


```

---

