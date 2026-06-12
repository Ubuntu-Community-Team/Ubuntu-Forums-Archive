---
title: "no sound in VLC, but it works in other programs"
date: 2008-06-30
forum: General Help
---

### Post by karasuman on 2008-06-30
I got irritated with the way Totem screws with your place in the video when you try to drag the bar, so I switched to VLC.  I didn't have any problem installing it, and the video works great...but there's no sound. 

I've checked the settings in alsamixer, and everything's normal.  The files still run in Totem.

Incidentally, I had this problem when I tried out Kaffeine, but I figured that Kaffeine was screwing up because I use gnome, not KDE.  Now I'm just confused.

I'd really appreciate any advice.

For the record, here's what I get when I type aplay -l in the terminal:

> beth@grumpy-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by manfer on 2008-06-30
First I suppose you don't have VLC muted. Did would be too obvious to be the problem.

[ATTACH]75843[/ATTACH]

If not that look in VLC the menu Options->Preferences. In the windows that appears, inspect audio preferences. Look if sound enable is ticked. Look into audio preferences, the out modules section and the subsection ALSA.

---

### Post by karasuman on 2008-06-30
I wish I just had it muted.  :)  Then things would be easy.

A lot of freezing/crashing seems to be going on as I change settings, or sometimes even if I just click "stop." Is that normal?  

Playing around with the options you've mentioned, the only thing that makes any difference is Audio Output Frequency, which by default is set to -1.  Changing this value makes things freeze and crash, but, when I restart, I have some sound if I put the value at 1 instead.  The sound is really jumpy and static-y, though.  If I set it to 2, 3, or 4, things are still like this.  If I set it to a really fun number like 33, though, the program crashes every time I try to play anything.  I haven't found a value that makes the sound normal.

This is the only setting that seems to be affecting anything.  I don't understand why everything sounds insane in this program but fine in Totem. :-/

---

### Post by chriswyatt on 2008-06-30
Have you installed the PULSE audio plugin for VLC?

```
sudo apt-get install vlc-plugin-pulse
```

Then enable it in Preferences under VLC Media Player: Audio -> Output Modules and make sure Advanced Options is selected (bottom right).  The rest should be obvious :P .

---

### Post by karasuman on 2008-06-30
Something is non-obvious to me.  :-/  I don't HAVE an option for Output Modules under Audio.  This seems to be version 0.8.6e Janus.  Is there a different version I could/should be using?

Under Preferences - Audio -Advanced Settings, I have the options to enable audio (checked), default audio volume, audio volume output step, audio output frequency, high quality audio resampling (checked), use S/PDIF when available (not checked, checking it doesn't seem to do much), Force detection of Dolby Surround (changing this doesn't do anything), Audio desynchronization compensation.

The other options I have under Preferences are Video, Input/Codecs, Stream Output, Advanced, Playlist, and Interface. None of the various settings here seem to be what you're talking about.

If I just choose the Audio tab (not the settings list), I have Audio Track, Audio Device, Audio Channels, Visualizations, Equalizer.  Only the last two are available if there's no file currently playing.  Changing the options under the other three doesn't do much, and there aren't many options; pick between Disable and Track 1; pick between mono and stereo; pick between stereo, reverse stereo, left, and right; respectively.

When I ran the command to get the pulse plugin, I got this as part of the response:

```
vlc-plugin-pulse is already the newest version.
vlc-plugin-pulse set to manually installed.

```

---

### Post by avtolle on 2008-06-30
Hmm, with advanced options, clicking on output modules in the left panel should bring up a panel to the right that tells you which one is being used. Mine says pulse audio (after I changed it long ago from something else and made the change permanent).

---

### Post by manfer on 2008-06-30
There is an arrow to the left of every option, audio, video, ..., to expand that option. Again speaking of Options->Preferences.

In audio there are three sections: filters, output modules, visualizations. Are you expanding it?

Have you looked in output modules section?

---

### Post by karasuman on 2008-06-30
Ahaha, don't I feel stupid.  Sorry about that.

I've found the output modules menu.  Changing it to Pulse doesn't make a difference in the quality of sound.  Just for kicks, I tried all the other; they all sound the same: awful.

---

### Post by mc4man on 2008-06-30
Just for the heck of it open vlc settings -> preferences and click reset all, ans. yes and _save._ Then reopen, ck. adv. options, expand audio, highlight output modules and in the dropdown change from default to alsa. _Click save_ and try.

---

### Post by karasuman on 2008-06-30
You're fabulous!  That worked.

Big thanks to everyone who spent their time helping me resolve this!  :)

---

### Post by ktamm on 2008-07-06
I also would like to say thank you, I had this same issue and mc4man's solution fixed my problem. 


Thanks again :)

---

### Post by AlexOslo on 2008-11-26
I am running Ubuntu 8.04 and have no audio, only video, in VLC and Movie Player respectively. Audio works fine in Amarok, though!

I tried following the instructions in this thread, without any of those operations working. I tried all the different settings under Audio -> Output options. The plugins are all installed.

For some reason, in the VLC player, on the Audio tab in the menu, by default it says "disabled". I set it to Track 1 instead, but then it switches back to disabled again when I restart VLC (but it makes no difference what I set it to anyway!).

Anyone got a clue on this?

Alex

For lack of response to this, I posted it in a new thread here: [http://ubuntuforums.org/showthread.php?t=996164](http://ubuntuforums.org/showthread.php?t=996164)

---

### Post by tkalfigo on 2008-12-12
Thanks mc4man. 
Original problem was: sound under VLC only through headphones but not through USB speakers but no problem with Totem (whose UI doesn't exactly thrill me).

Resetting to defaults, before setting own preferences did the thing (enough sweating my ears off with a set of terrible headphones)


Edit: Careful when opening up a second VLC. Do not freak out by the sound going to the headphones again. It seems that only one instance can occupy the USB speakers (USB protocol thing or linux driver?). Your saved preferences still hold if you close all and restart VLC. Hope that helps.

---

