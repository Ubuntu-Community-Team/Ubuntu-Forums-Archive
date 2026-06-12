---
title: "no sound at all"
date: 2007-12-17
forum: General Help
---

### Post by RandomXcore on 2007-12-17
I was playing a playlist using Mplayer when suddenly the sound stopped working.
then i realised that the sound wasnt working for anything in my computer.

for example when i played an audio file or a flash video file or video streamed through youtube, there was video and absolutely no sound.

I booted GEEXBOX to see if the sound worked in that and it did so my soundcard was working fine.

But I cannot work out what is wrong with the audio when i run my computer normally


These are the details.

OS : gNewSense (iso linux)
serenity@serenity-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:02.0 Communication controller: Agere Systems: Unknown device 0620

serenity@serenity-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]  Subdevices: 1/1
  Subdevice #0: subdevice #0

serenity@serenity-desktop:~$ dpkg -l |grep alsa
ii  alsa-base                         1.0.10-4ubuntu4                     ALSA driver configuration files
ii  alsa-oss                          1.0.10-1                     ALSA wrapper for OSS applications
ii  alsa-source                       1.0.10-4ubuntu4                     ALSA driver sources
ii  alsa-utils                        1.0.10-1ubuntu14                     ALSA utilities
ii  alsaplayer-common                 0.99.76-7ubuntu2                     PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                    0.99.76-7ubuntu2                     PCM player designed for ALSA (GTK version)
ii  alsaplayer-oss                    0.99.76-7ubuntu2                     PCM player designed for ALSA (OSS output mod
ii  gstreamer0.10-alsa                0.10.7-0ubuntu4                     GStreamer plugin for ALSA
ii  gstreamer0.8-alsa                 0.8.12-1ubuntu2                     ALSA plugin for GStreamer
ii  libesd-alsa0                      0.2.36-3ubuntu3                     Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                1.10.0-1ubuntu1                     Portable Windows Library Audio Plugin for th
rc  libsdl1.2debian-alsa              1.2.9-0.0ubuntu2                     Simple DirectMedia Layer (with X11 and ALSA
ii  vlc-plugin-alsa                   0.8.4.debian-1ubuntu6.1                     ALSA audio output plugin for VLC
serenity@serenity-desktop:~$

:confused:can anyone help me figure out how i need to fix my sound???????:(:(:(:(:(

---

### Post by flonomendo on 2007-12-18
Bumping.

I am having a similar problem, sound will not work for anything in Ubuntu... but back in my Windows boot everything works just fine.  Using Gutsy as well.  And, mine suddenly stopped working just like his did... I restarted and booted back into Gutsy and BAM no more sound.

So a fix/solution to this weird problem would help out a lot.  Thanks.

---

### Post by RandomXcore on 2007-12-18
yes, please help us!!

---

### Post by zakirs on 2007-12-18
hey try reading first post in this blog sry i feel lazy to write whole thing here :(
 [http://luvlinux.blogspot.com/](http://luvlinux.blogspot.com/)

---

### Post by RandomXcore on 2007-12-18
> **RandomXcore said:**
> I was playing a playlist using Mplayer when suddenly the sound stopped working.
then i realised that the sound wasnt working for anything in my computer.

for example when i played an audio file or a flash video file or video streamed through youtube, there was video and absolutely no sound.

I booted GEEXBOX to see if the sound worked in that and it did so my soundcard was working fine.

But I cannot work out what is wrong with the audio when i run my computer normally


These are the details.

OS : gNewSense (iso linux)
serenity@serenity-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:02.0 Communication controller: Agere Systems: Unknown device 0620

serenity@serenity-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]  Subdevices: 1/1
  Subdevice #0: subdevice #0

serenity@serenity-desktop:~$ dpkg -l |grep alsa
ii  alsa-base                         1.0.10-4ubuntu4                     ALSA driver configuration files
ii  alsa-oss                          1.0.10-1                     ALSA wrapper for OSS applications
ii  alsa-source                       1.0.10-4ubuntu4                     ALSA driver sources
ii  alsa-utils                        1.0.10-1ubuntu14                     ALSA utilities
ii  alsaplayer-common                 0.99.76-7ubuntu2                     PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                    0.99.76-7ubuntu2                     PCM player designed for ALSA (GTK version)
ii  alsaplayer-oss                    0.99.76-7ubuntu2                     PCM player designed for ALSA (OSS output mod
ii  gstreamer0.10-alsa                0.10.7-0ubuntu4                     GStreamer plugin for ALSA
ii  gstreamer0.8-alsa                 0.8.12-1ubuntu2                     ALSA plugin for GStreamer
ii  libesd-alsa0                      0.2.36-3ubuntu3                     Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                1.10.0-1ubuntu1                     Portable Windows Library Audio Plugin for th
rc  libsdl1.2debian-alsa              1.2.9-0.0ubuntu2                     Simple DirectMedia Layer (with X11 and ALSA
ii  vlc-plugin-alsa                   0.8.4.debian-1ubuntu6.1                     ALSA audio output plugin for VLC
serenity@serenity-desktop:~$

:confused:can anyone help me figure out how i need to fix my sound???????:(:(:(:(:(

I also have this come up in my terminal when i am trying to play a video,
(the video is fine, but of course there is no audio

[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-lib: pcm_hw.c:1217:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 22050Hz 2ch s16le (2 bytes per sample)

i hope this will help someone to figure out what is wrong here!!!
thanks

---

### Post by RandomXcore on 2008-01-28
UPDATE: Now it doesnt even say that message anymore, it just opens audio file and plays away like it was normally , you know, with sound and everything, but the erie thing is,..... there is no sound..

---

### Post by Helios38 on 2008-01-28
try going into System > administration > sound

its either administration or preferences.


and see whats going on there.

you may have already done that but im just giving it a shot.

---

### Post by RandomXcore on 2008-01-28
> **RandomXcore said:**
> UPDATE: Now it doesnt even say that message anymore, it just opens audio file and plays away like it was normally , you know, with sound and everything, but the erie thing is,..... there is no sound..

I took the liberty of making a pastebin to show you.. 
here is me trying to play a song through mplayer on terminal.  [http://pastebin.com/f6a3c341c](http://pastebin.com/f6a3c341c)

---

### Post by RandomXcore on 2008-01-28
> **Helios38 said:**
> try going into System > administration > sound

its either administration or preferences.


and see whats going on there.

you may have already done that but im just giving it a shot.

and what do i do then? it seems normal.. 

on terminal i tried to check the sound on alsamixer. it would come up with the message 
"No mixer elems found."
 it used to give me the volume control but now.. weird huh..

---

### Post by RandomXcore on 2008-02-16
> **RandomXcore said:**
> UPDATE: Now it doesnt even say that message anymore, it just opens audio file and plays away like it was normally , you know, with sound and everything, but the erie thing is,..... there is no sound..

this is for those who have this problem, dont know if it will help you coz every situation is different.

ok this is obvious i know, but im a newbie and i took a while to figure this out so yeh.

the reason that you cant get any sound is because another process is using your audio file /dev/dsp. as it says in the output in terminal when youre playing a file on mplayer.

if you want your sound back, you have to find and terminate the process that is using that file so that mplayer can access it.

for example, i use flash on websites and when i have that web page open, (my browser is firefox burning dog) and im streaming media from youtube, if i open terminal and start to play another audio file (not at the same time of course) it will give the message that /dev/dsp is already in use. So if i close the web browser, then mplayer will pick up the audio again.

---

### Post by RandomXcore on 2008-03-29
Ok now my sound has gone again, i dont know what i have done. 

it has done this to me 3 times now!! 

i thought i solved it last time, but this time there is no other processes using the audio file /dev/dsp.

i wonder how i can get it back again????

can anyone help me??

---

