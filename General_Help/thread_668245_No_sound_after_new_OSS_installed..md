---
title: "No sound after new OSS installed."
date: 2008-01-15
forum: General Help
---

### Post by steliosgr on 2008-01-15
Hello i have a problem after i'v installed the latest OSS.
I havent sound on my Ubuntu and the sound icon have a red X icon that mean i have no sound.

i have the M-audio Delta LT soundcard .

On osstest im getting sound.

But i cant listen anysound on my system like mp3's web etc.

im wondering if i must blacklist the old alsa driver, but i dont know how.

Plz help me im using windows to listen my Mp3's :((

---

### Post by Yellow Pasque on 2008-01-15
Have you gone into the sound prefs and selected OSS as the default for sound playback? Have you changed the output plugin to OSS in your media player app?

The gnome sound/volume control is incompatible with OSS4 (hence the redX). You should be using the ossxmix program for mixer control now. Also, someone was nice enough to write a patch to restore media key/mouse wheel functionality.

> 8. You'll need to right-click on and remove the mixer/volume control icon from the panel.
9. In a terminal, run the ossinfo command. The mixer devices are numbered, so note the number of the mixer device you want to control.
10. Add a new custom application launcher to the panel that runs the command: ossxmix -d<mixer number you got in step 9> That's ossxmix, not ossmix, and the command will default to -d0 if you don't add a switch. Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon.

> Volume Control Patch[/B] The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's [patch](http://4front-tech.com/forum/viewtopic.php?t=2357&highlight=). I've also built and attached an AMD64 version to this post. Note that this patch was updated on 1/8/08, so if you tried it before then and it didn't work, try again.
Also, if you'd prefer to map commands to your shortcut keys, [here are some scripts to use](http://wiki.archlinux.org/index.php/OSSt) (at the bottom of the page).

---

### Post by TidusBlade on 2008-01-15
I had a similar annoying problem :S
Depending on what program you use for music, I use Amarok, and you can change the output, so it depends. I think many programs can only use ALSA, seen a few, so it might be safer and stick with ALSA, and use "alsaoss" to emulate OSS I think.

---

### Post by steliosgr on 2008-01-15
Ty all for your help :D i didnt try nothing because i unistalled the oss and the sound came back :D

Im wondering wich is better to use Alsa or OSS?

The reason were i'v installed oss was to have sound on Wine.

---

### Post by Yellow Pasque on 2008-01-15
> **TidusBlade said:**
> I had a similar annoying problem :S
Depending on what program you use for music, I use Amarok, and you can change the output, so it depends. I think many programs can only use ALSA, seen a few, so it might be safer and stick with ALSA, and use "alsaoss" to emulate OSS I think.
A lot of programs are written for OSS, because it's a helluva lot easier to write a program using OSS than ALSA (As a former programmer, I can appreciate that the OSS API is well-documented and relies on library functions, whereas writing ALSA code would depend on such fun things as mutex's).

Also, OSS4 works better on my M-Audio Revo (no volume bugs, headphone jack works, etc.) and the mixer pwns.

---

### Post by SeaJey on 2008-01-16
> Also, OSS4 works better on my M-Audio Revo (no volume bugs, headphone jack works, etc.)
Well, there is one bug - using kubuntu 7.10, M-audio revo 5.1, oss-linux v4 build 1012 (or later), headphone output and vmix with default  value vmix0-src = "fast" - you have a "pleasure" to hear (and see via ossxmix) regular clicks in right stereo channel.
The cure is to set "low", "high" or any other value to vmix0-src

---

### Post by Yellow Pasque on 2008-01-16
> **SeaJey said:**
> Well, there is one bug - using kubuntu 7.10, M-audio revo 5.1, oss-linux v4 build 1012 (or later), headphone output and vmix with default  value vmix0-src = "fast" - you have a "pleasure" to hear (and see via ossxmix) regular clicks in right stereo channel.
The cure is to set "low", "high" or any other value to vmix0-src
:? I don't have this problem (in neither Ubuntu64 or Arch64). I'm using a Logitech MX1000 Wireless mouse

---

### Post by SeaJey on 2008-01-16
> Well, there is one bug - using kubuntu 7.10 i386, M-audio revo 5.1, oss-linux v4 build 1012 (or older), headphone output and vmix with default value vmix0-src = "fast" - you have a "pleasure" to hear (and see via ossxmix) regular "clicks" in right stereo channel.
The cure is to set "low", "high" or any other value to vmix0-src
Fixed

"Clicks" in the mean - quick noise, flick, fillip
See [also](http://www.4front-tech.com/forum/viewtopic.php?t=2362)

---

### Post by akwatve on 2008-01-23
I too have this problem. I dont hear ANYTHING but I can see things playing in the mixer..
osstest returns success... amarok and xmms do not complain at all while playing. KDE control center is set to use OSS but............... I dont hear anything :-(

I have no clue whats happening ...

One observation: In my mixer the channel numbering  start from 9(i.e. pcm8, pcm9....pcm15) Is that normal ? Shouldnt it start from pcm0 ?
Also what are vmix0-* options ? especially what does vmix0-src mean/do ?

---

