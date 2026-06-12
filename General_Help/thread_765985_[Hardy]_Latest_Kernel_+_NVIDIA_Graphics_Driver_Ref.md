---
title: "[Hardy] Latest Kernel + NVIDIA Graphics Driver Refuses to Work"
date: 2008-04-24
forum: General Help
---

### Post by GenuineXP on 2008-04-24
So Gutsy seemed to handle my NVIDIA GeForce 6600 GT wonderfully (as did Feisty), but Hardy chews it up, spits and out, and vomits all over it just for kicks.

Well, okay, it's not *that* bad, but I cannot for the life of me get X configured when using the latest kernel for Hardy. Instead, I have to wait for GRUB to display a the OS selection menu and choose an older kernel. This actually seems to confuse some software that requires packages compiled for specific kernel versions.

Whenever I boot normally (i.e., I don't manually select a kernel), I get a tiny 800x600 or sometimes even 640x480 display. Using the old displayconfig-gtk utility along with NVIDIA's control panel yields nothing (the control panel claims I have no NVIDIA X driver). Installing both nvidia-glx and nvidia-glx-new yield no results.

How in the world can I fix this? It was an issues when Hardy was still in Beta, than the RC came out, and now even with the final release I still cannot fire up my graphics card!

Am I the only one who finds the concept of "restricted drivers" a little odd and annoying, btw?

Anyway, any help at all is greatly appreciated; I hate cursing when I miss the GRUB screen and boot into low graphics mode just about everyday.

Thanks!

---

### Post by lrich28 on 2008-04-24
Go to synaptic and enable third party repos.  Then search for nvidia and select the correct driver.  You will then have to enable it through the hardware driver page System->Administration->Hardware drivers.

---

### Post by GenuineXP on 2008-04-25
Thanks, but this doesn't seem to be working. Searching for "nvidia" with Synaptic after adding third party sources causes a few new hits to show up, but no new drivers as far as I can tell. The Hardware Drivers applet doesn't even list a driver for my graphics card! Strange.

Thanks again.

---

### Post by lrich28 on 2008-04-25
Well, when I had this problem I added the third party repos and then installed nvidia-glx-new.

---

### Post by GenuineXP on 2008-04-25
Hm, what graphics card do you have? Is it also a GeForce 6 series card?

It think I've had the nvidia-glx-new package installed since I first slapped the Hardy Beta on my box. It was the kernel update that seemed to break my display/graphics.

Does anyone know if there's a kernel/driver bug? Simply reverting to an older kernel seems to make the problems disappear. However, I have some programs, including VirtualBox OSE, that depend on the more recent kernel.

Thanks again for the input; I appreciate it.

---

### Post by SnakeHips on 2008-04-25
I'm running the GeForce6200 on Hardy 2.6.24-16 generic 64bit - works fine.

menu/system/hardware drivers - enable restricted drivers - is that checked ?

---

### Post by GenuineXP on 2008-04-25
No graphics driver is listed to enable when I boot into the 2.6.24-16 (latest) kernel.

In other kernels, it is listed and enabled (and works).

I'd like to avoid manually installing drivers from a binary (from NVIDIA's website, etc.), but I'm worried I may have to do this.

Any other ideas?

**EDIT:**
One thing I noticed is that my monitor is receiving a full resolution (1280x1024@60Hz) signal, but the display resolution in Ubuntu is currently 800x600@61Hz (the frequency is *always* incorrect and has been since Ubuntu Feisty). Weird.

---

### Post by SnakeHips on 2008-04-25
Hmmmm.....

menu/apps/system/software sources - 

you have "proprietary drivers for devices (restricted)" enabled right?

---

### Post by xjgnsdof on 2008-04-25
I have a similar problem with my 8800GTS 512 and 22" widescreen Acer: a resolution too small for comfort. Manually installing the driver by stopping the X session doesn't work, and automatically installing the driver through Envy doesn't work either. Strange thing is, Compiz works perfectly; it's just the resolution that sucks.

---

### Post by GenuineXP on 2008-04-25
> **SnakeHips said:**
> 
you have "proprietary drivers for devices (restricted)" enabled right?
Yep, enabled.

Is there a problem with the kernel module or something? When I try to modprobe the nvidia module, I get this.

```

sean@harpuia:~$ sudo modprobe nvidia
[sudo] password for sean: 
FATAL: Error running install command for nvidia
sean@harpuia:~$ dmesg | tail
[  183.639961] Bluetooth: RFCOMM ver 1.8
[  185.199772] Registered led device: b43-phy0:tx
[  185.200225] Registered led device: b43-phy0:rx
[  185.200609] Registered led device: b43-phy0:radio
[  189.382812] NET: Registered protocol family 17
[  194.542372] NET: Registered protocol family 10
[  194.542550] lo: Disabled Privacy Extensions
[  194.545051] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  194.545850] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  205.363740] eth0: no IPv6 routers present
sean@harpuia:~$ 

```

I'm not sure what this means. As you can see, dmesg doesn't seem to get any NVIDIA related entries either.

Just in case anyone has any ideas or theories, here's my lspci output.

```

sean@harpuia:~$ lspci | grep -i nvidia
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
sean@harpuia:~$ 

```

Any more assistance is appreciated; I'm getting very tired of staring at a fuzzy low resolution display with no rendering support! I can't get my work done.

---

### Post by SnakeHips on 2008-04-25
...you may have trod on a bug?

try this?

if (restricted drivers) is checked in apps/system/hardware then disable

remove the following from synaptic
nvidia-glx-common
nvidia-kernel-common
xserver-xorg-video-nv
nvidia settings

shutdown and _cold_ boot your pc

any restart probs then go safe mode (vesa)

login and goto apps/system/hardware and enable restricted drivers - what happens?

---

### Post by xjgnsdof on 2008-04-25
Through my own misadventure, I had to do a fresh installation of Hardy -16. My 8800GTS 512 worked with the native drivers--my resolution was at its native 1680x1050--but I had to install nvidia-glx-new. Once I did that (and it did take a while, given that people all over the world were likely bogging down the repos), my video card worked perfectly. On a side note, my Linksys WUSB54Gv4 wireless adapter worked automatically, as did the Pulse audio server. Give a fresh installation a try.

---

### Post by GenuineXP on 2008-04-25
Well, after removing all the NVIDIA and restricted driver related packages, everything seems to work now!

Another thing, instead of installing the "generic" version of the restricted drivers package, I installed i386 after noticing the kernel choice at the top of the GRUB menu said i386 instead of generic (as all other entries do).

Thanks for all the help!

---

### Post by GenuineXP on 2008-04-25
**IMPORTANT:**

Whoa, it seems the whole problem was having the i386 kernel image rather than the generic image. I thought it was a bit strange; I just noticed it in my GRUB boot list yesterday (I also had the generic kernel image, but it wasn't the default selection).

The restricted drivers package for the i386 image was never installed. Just installing that package manually "fixed" the problem, but the i386 image causes many others, including no sound! (There's another thread out there about that right now).

It seems the best fix for folks experiencing the same issue is to **remove the i386 kernel image** and **install and use the generic kernel image** followed by making sure restricted driver packages are installed for that kernel.

---

### Post by eys on 2008-04-25
Hi,
Try install Envy.

---

### Post by ExBuM on 2008-04-26
Gah this nvidia driver is really frustrating me. I've tried installing 173.08 from the official nvidia site, EnvyNG, and linux-restricted-modules but nothing works. IF I enable anything nvidia from the restricted drivers manager, I boot into low resolution mode. Compiz and other desktop effects don't work either. Is there any way to enable my nvidia card?

---

### Post by whistlerspa on 2008-04-26
> **GenuineXP said:**
> **IMPORTANT:**

Whoa, it seems the whole problem was having the i386 kernel image rather than the generic image. I thought it was a bit strange; I just noticed it in my GRUB boot list yesterday (I also had the generic kernel image, but it wasn't the default selection).

The restricted drivers package for the i386 image was never installed. Just installing that package manually "fixed" the problem, but the i386 image causes many others, including no sound! (There's another thread out there about that right now).

It seems the best fix for folks experiencing the same issue is to [SIZE="4"]**remove the i386 kernel image**[/SIZE] and **install and use the generic kernel image** followed by making sure restricted driver packages are installed for that kernel.

How do you do that?

---

### Post by whistlerspa on 2008-04-26
> **GenuineXP said:**
> **IMPORTANT:**

Whoa, it seems the whole problem was having the i386 kernel image rather than the generic image. I thought it was a bit strange; I just noticed it in my GRUB boot list yesterday (I also had the generic kernel image, but it wasn't the default selection).

The restricted drivers package for the i386 image was never installed. Just installing that package manually "fixed" the problem, but the i386 image causes many others, including no sound! (There's another thread out there about that right now).

It seems the best fix for folks experiencing the same issue is to [SIZE="4"]**remove the i386 kernel image**[/SIZE] and **install and use the generic kernel image** followed by making sure restricted driver packages are installed for that kernel.

How do you do that? In any case I had the same issue with the 64 bit kernal.

---

### Post by nbayiha on 2008-04-30
GenuineXP can u tell us how u did ur trick ,cause i am having the same problem and instaling the driver form the nvidia page didn't do the think. And i don't want to do a fresh installation cause i just have to many program and i don't want to compile them again or install them. So please Just tell us how to do it :D

---

### Post by Nunu on 2008-04-30
Did you guys runn nvidia-xconfig  and nvidia-settings from terminal after installing nvidia-glx-new?

---

### Post by nbayiha on 2008-04-30
Actually i did manage to install the new driver of nvidia. the one from the repository wasn't working for me and i didn't want to do a fresh installation. 
I will post actually what i did in case it can help you whistlerspa or some other fellas.

First make sure everything comporting nvidia is not install, if so uninstall them from the repository(nvidia-setting nvidia-glx nvidia-glx-new....) , just remove all of them.
now follow those command step by step , better if u write it down cause we are going to kill the server.


first download the driver from this link [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and save it wherever u want i did save mine in the desktop.

now the funny part

 u go to disable the nvidia driver in the repository ,so they won't have conflicted problem with the one we download, by  doing this

> gksudo gedit /etc/default/linux-restricted-modules-common 

edit the DISABLED_MODULES line so it will look like this
>  DISABLED_MODULES="nv nvidia_new" 

1-first we kill the server 

> sudo /etc/init.d/gdm stop
if u have some problem after that just do ctrl+alt+f1orf2orf5
u will be asked to log in

2-now go to the folder where u dowload the nvidia driver mine was in the Desktop

>  cd /home/xxx/Desktop 

3- level up ur telinit
 
> sudo telinit 3

4- then run the driver
 
> sudo sh NVIDIA(.... the name of the driver u downloaded)
 and accept everything they ask  you.

5- after just 

> sudo reboot

and it should do the think.
In case if he didnt work write back.

---

### Post by krak on 2008-05-08
@ nbayiha
Your's solution works fine !
Thank You

---

### Post by tarsius4 on 2008-05-08
@ nbayiha

Worked for me too! (Although not without a little bit of trouble).
Now my audio has stopped working--but I think trading it for a decent resolution is fair.

---

### Post by nbayiha on 2008-05-08
Tarsius,  your sound stop working :(? Does that means u don't have any sound when u try to watch a movie ? If it's the case , are u using alsa or OSS ? try to open ur player(mplayer or vlc or smplayer...) from the terminal and open a movie and post the result here , so we can try to figure out where is the problem :popcorn:

---

### Post by tarsius4 on 2008-05-08
> 
~$ lspci
...
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
...


There's my audio hardware, but in Menu>System>Preferences>Multimedia Systems, none of the plugins for Default Input/Default Output have a corresponding "Device".  For instance, if I select "ALSA" for Default Output, then the Device field remains grayed out and says "None".  Clicking "Test" pops up a box that says "ALSA - Advanced Linux Sound Architecture: Could not open audio device for playback."


Finally, here is the output of launching mplayer from the terminal:
> 
~$ mplayer Lecture-4a.avi 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-52 (Family: 15, Model: 72, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Lecture-4a.avi.
AVI file format detected.
[aviheader) Video stream found, -vid 0
[aviheader) Audio stream found, -aid 1
VIDEO:  [DIV3)  320x240  24bpp  29.970 fps  910.4 kbps (111.1 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: (ffmpeg) FFmpeg's libavcodec codec family
Selected video codec: [ffdivx) vfm: ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad) libmad mpeg audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 64.0 kbit/8.33% (ratio: 8000->96000)
Selected audio codec: [mad) afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse) Failed to connect to server: Invalid argument
[AO_ALSA) alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA) alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA) alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA) alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA) alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA) alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA) alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA) alsa-lib: pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA) Playback open error: No such file or directory
[AO OSS) audio_setup: Can't open audio device /dev/dsp: No such file or directory
[AO_ALSA) alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA) alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA) alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA) alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA) alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA) alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA) alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA) alsa-lib: pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA) Playback open error: No such file or directory
[AO ARTS) can't connect to aRts soundserver
[AO ESD) latency: [server: 0.37s, net: 0.00s] (adjust 0.37s)
AO: [esd) 44100Hz 1ch s16le (2 bytes per sample)
Starting playback...
2 bytes of audio data lost due to buffer overflow, len = 20
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv) 320x240 => 320x240 Planar YV12 
2 bytes of audio data lost due to buffer overflow, len = 2?,?% 0 0 
2 bytes of audio data lost due to buffer overflow, len = 2?,?% 0 0 
2 bytes of audio data lost due to buffer overflow, len = 2?,?% 0 0 
2 bytes of audio data lost due to buffer overflow, len = 2?,?% 0 0 
2 bytes of audio data lost due to buffer overflow, len = 2?,?% 0 0 
...


By the way, this was definitely working back when the video driver was broken, but I'm not sure what sound system I was using before.

---

### Post by tarsius4 on 2008-05-08
I just got the audio working thanks to this post:
[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

Note that this is specific to the HP tx1000 series laptop, but for people out there with issues with sound, it might be useful to check if there are multiple versions of the same snd- module gumming up the works.

---

### Post by nbayiha on 2008-05-09
Nice that u did manage to find the answer around :guitar:. By the way did u give a try to pulseaudio it's supposing to resolve those kind of problem.

[http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio) :KS

---

### Post by outferno on 2008-05-09
> **nbayiha said:**
> Actually i did manage to install the new driver of nvidia. the one from the repository wasn't working for me and i didn't want to do a fresh installation. 
I will post actually what i did in case it can help you whistlerspa or some other fellas.

First make sure everything comporting nvidia is not install, if so uninstall them from the repository(nvidia-setting nvidia-glx nvidia-glx-new....) , just remove all of them.
now follow those command step by step , better if u write it down cause we are going to kill the server.


first download the driver from this link [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and save it wherever u want i did save mine in the desktop.

now the funny part

 u go to disable the nvidia driver in the repository ,so they won't have conflicted problem with the one we download, by  doing this



edit the DISABLED_MODULES line so it will look like this


1-first we kill the server 


if u have some problem after that just do ctrl+alt+f1orf2orf5
u will be asked to log in

2-now go to the folder where u dowload the nvidia driver mine was in the Desktop



3- level up ur telinit
 


4- then run the driver
 

 and accept everything they ask  you.

5- after just 



and it should do the think.
In case if he didnt work write back.


Thank you so much for this fix!  It worked wonderfully on my tx1000z with the GeForce 6150!

---

### Post by zorba_g on 2008-05-22
Thank you very much for this. I have been trying to get this working for several days. Basically I too had the problem where I had not updated the GRUB menu during the upgrade process; I had been trying various combinations of the advice in this thread but on the Gutsy kernel. Once I fixed that, I followed the advice given by nbayiha almost exactly (I used *sudo /etc/init.d/gdm stop* instead of *sudo /etc/init.d/gdm start*), rebooted and lo and behold, nvidia logo, compiz and correct screen res all returned! Thanks ever so much.

Z

Edit: this was on a Clevo D900K athlon x2 4800 with Geforce Go 7800GTX and 1680x1050 screen, upgrading from 7.10 to 8.04 in case anyone has the same problem

---

### Post by Zer0Nin3r on 2008-05-22
> **GenuineXP said:**
> So Gutsy seemed to handle my NVIDIA GeForce 6600 GT wonderfully (as did Feisty), but Hardy chews it up, spits and out, and vomits all over it just for kicks.

Well, okay, it's not *that* bad, but I cannot for the life of me get X configured when using the latest kernel for Hardy. Instead, I have to wait for GRUB to display a the OS selection menu and choose an older kernel. This actually seems to confuse some software that requires packages compiled for specific kernel versions.

Whenever I boot normally (i.e., I don't manually select a kernel), I get a tiny 800x600 or sometimes even 640x480 display. Using the old displayconfig-gtk utility along with NVIDIA's control panel yields nothing (the control panel claims I have no NVIDIA X driver). Installing both nvidia-glx and nvidia-glx-new yield no results.

How in the world can I fix this? It was an issues when Hardy was still in Beta, than the RC came out, and now even with the final release I still cannot fire up my graphics card!

Am I the only one who finds the concept of "restricted drivers" a little odd and annoying, btw?

Anyway, any help at all is greatly appreciated; I hate cursing when I miss the GRUB screen and boot into low graphics mode just about everyday.

Thanks!
Been having the same problems ever since my upgrade.  I have made some progress [here]("http://ubuntuforums.org/showthread.php?t=792276").

---

### Post by Cuppa-Chino on 2008-06-06
> **outferno said:**
> Thank you so much for this fix!  It worked wonderfully on my tx1000z with the GeForce 6150!

no dice when ever my computer starts up it finds Nvidia drivers on first boot but then goes into "low graphics mode" tx1000 hewlett packard, cannot get even get back to a nv driver now... 

anybody else had the one boot issue?

---

### Post by briandu on 2008-06-06
follow this exactly, it works for me on latest

[http://ubuntuforums.org/showthread.p...80#post5064980]("http://ubuntuforums.org/showthread.php?p=5064980#post5064980") msg #430

---

