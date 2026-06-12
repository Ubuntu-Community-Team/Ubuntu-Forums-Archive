---
title: "Just wondering"
date: 2012-11-07
forum: General Help
---

### Post by zealibib slaughter on 2012-11-07
Ok I got a question which has been troubling me for a few days now.  Both me and my friend run Linux (me Ubuntu Studio 12.04-64 and he has Mint 13-i386 with xfce) He is able to run open arena, sauerbraten, assault cube, ect. I can't. His system is an older dell Intel P4 single core 3.2ghz with 1Gb ddr ram and Intel onboard graphics. Mine is a frankenstien of random parts with a asus motherboard Intel 3.2 dual core, 1GB ddr2 ram, and a nvidia 6200oc graphics card. Could the low latency kernel have something to do with the issues of being able to run these games?

---

### Post by snowpine on 2012-11-07
"I can't" and "the issues" isn't enough level of detail for anyone to help you troubleshoot the problem in a meaningful way, I'm afraid.

It is very easy to test your theory that the real-time kernel is causing the problem. You can install the generic kernel from Software Center, reboot, and switch kernels from the GRUB boot menu. Kernels that do not give good results can be uninstalled through Software Center as well.

---

### Post by zealibib slaughter on 2012-11-07
I didn't think about installing another kernel thanks I will try that.  The issues I have is complete system lockup, example - Assault Cube. Game loads to splash screen and system becomes unresponsive. I have to sak the xserver with alt-sysrq-k to regain control.

---

### Post by sandyd on 2012-11-07
> **zealibib slaughter said:**
> Ok I got a question which has been troubling me for a few days now.  Both me and my friend run Linux (me Ubuntu Studio 12.04-64 and he has Mint 13-i386 with xfce) He is able to run open arena, sauerbraten, assault cube, ect. I can't. His system is an older dell Intel P4 single core 3.2ghz with 1Gb ddr ram and Intel onboard graphics. Mine is a frankenstien of random parts with a asus motherboard Intel 3.2 dual core, 1GB ddr2 ram, and a nvidia 6200oc graphics card. Could the low latency kernel have something to do with the issues of being able to run these games?What kernel are you using?
Can you post the output of```
uname -a
```

Also, the reason behind the RT/lowlatency kernels, and if you really need it: [https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)
Also, as far as I know, the RT patch has lagged behind for a while. For instrctions on how to compile the RT Kernel wit the newest patches, see [http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel](http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel). Your problem may be fixed with a newer patch.

---

### Post by zealibib slaughter on 2012-11-07
output of uname -a

Linux Motherbrain-Master 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I need the low latency kernel for audio production. The generic kernel produces a lag between the instruments and audio output.

I'm investigating into compiling the latest kernel with rt/ll patches now. Tried installing 3.2.0-34 generic but had same problem.

---

### Post by snowpine on 2012-11-07
I guess my point was, you could use the low-latency kernel for audio production and the generic kernel for games?

---

### Post by zealibib slaughter on 2012-11-07
sorry meant the generic kernel gives me the same problem with games, system freezes.

---

### Post by holycow131415 on 2012-11-07
type the game in the terminal, and report back any errors that may appear in the terminal. Also, have you checked the additional drivers gui to see if there is a driver you need to enable for your nvidia card.

---

### Post by zealibib slaughter on 2012-11-07
Using the recommended nvidia driver

terminal output of assaultcube
```
current locale: en_US.UTF-8
init: sdl
init: net
init: world
init: video: sdl
init: video: mode
init: video: misc
init: gl
Renderer: GeForce 6200/PCI/SSE2 (NVIDIA Corporation)
Driver: 2.1.2 NVIDIA 295.40
init: console
init: sound
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Audio devices: PulseAudio Default, ALSA Default, PortAudio Default
Sound: PulseAudio Default / OpenAL Soft (OpenAL Community)
Driver: 1.1 ALSOFT 1.13
init: cfg
init: models
init: docs
init: localconnect
read map packages/maps/official/ac_complex.cgz rev 3 (3682 milliseconds)
Industrial Zone - by makkE
loaded textures (207 milliseconds)
loaded mapmodels (117 milliseconds)
loaded mapsounds (805 milliseconds)
game mode is "TDM"
init: mainloop
Welcome to AssaultCube
Developed by 'Rabid Viper Productions'

Use the below menu to change some necessary settings...

Further help & information can be found in your README, which is inside your AssaultCube directory.


```

with assault cube and jackd running memory usage is around 600mb (a little more than half) some swap usage about 100 mb and both cores operating between 75 to 100%

---

