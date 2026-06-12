---
title: "How to Completely remove PulseAudio?"
date: 2008-06-26
forum: General Help
---

### Post by sunshine12 on 2008-06-26
Can anyone please tell me how to completely remove PulseAudio from my computer. PulseAudio is creating many problems in Audacity, and normal playback.

when I start movie or video clip in vlc or something than there isn't sound at first and terminal shows some error messages regarding PulseAudio and jack etc...

I want to remove it completely. Please help.

---

### Post by iaculallad on 2008-06-26
> **sunshine12 said:**
> Can anyone please tell me how to completely remove PulseAudio from my computer. PulseAudio is creating many problems in Audacity, and normal playback.

when I start movie or video clip in vlc or something than there isn't sound at first and terminal shows some error messages regarding PulseAudio and jack etc...

I want to remove it completely. Please help.

On your terminal:

```
sudo apt-get install esound
sudo apt-get remove pulseaudio

```

---

### Post by sunshine12 on 2008-06-26
Done that and it removed pulseaudio...

But when I start playing some video files than the problem persists, when started from the terminal then it shows the following message...


admin@admin-desktop:~$ vlc
VLC media player 0.8.6e Janus
[00000360] pulse audio output error: Failed to connect to server: Connection refused
[00000360] pulse audio output error: Pulse initialization failed
*** PULSEAUDIO: Unable to connect: Connection refused
[00000360] jack audio output error: failed to connect to JACK server
[00000284] main playlist: stopping playback


So, Please tell me How to get rid of this Pulseaudio??? Pulseaudio is considered a new feature in hardy but I think it creating more problems than anything!!! Everything was fine in feisty and gusty...

Thanks and please suggest how to remove "completely" pulseaudio..

---

### Post by sdennie on 2008-06-26
Rather than removing it, have you tried to just make everything use ALSA instead?  System->Preferences->Sound and change everything to ALSA (You may have to do that within the individual apps you are using as well).  Alternatively, you could read [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and see if you could get pulse audio working properly.

---

### Post by iaculallad on 2008-06-26
I haven't got any more idea on how to completely remove pulseaudio. But before you completely remove it,
Try to add user mpd to the pulseaudio groups:

```
sudo usermod -a -G pulse-access mpd
sudo usermod -a -G pulse mpd
sudo usermod -a -G pulse-rt mpd
```

Then test your VLC if it displays error.

---

### Post by sunshine12 on 2008-06-27
> **iaculallad said:**
> I haven't got any more idea on how to completely remove pulseaudio. But before you completely remove it,
Try to add user mpd to the pulseaudio groups:

```
sudo usermod -a -G pulse-access mpd
sudo usermod -a -G pulse mpd
sudo usermod -a -G pulse-rt mpd
```

Then test your VLC if it displays error.

Will do it and tell the results, if this works with Audacity too?
I think there is some problems with audacity and pulseaudio. What exactly is the pulseaudio?? ALSA was working fine in gutsy, why this pulseaudio is added?

---

### Post by zmjjmz on 2008-06-30
Pulseaudio is technically better, it just doesn't work with everything yet, so some applications won't send sound to it.
ALSA worked fine for me too, but for some people Pulseaudio is a good thing.

---

### Post by susancragin on 2009-05-27
I think you have to do this:

sudo apt-get purge pulseaudio
sudo apt-get install esound

Otherwise the configuration files remain.

---

### Post by colau on 2009-05-27
Is there any command to know which sound playback is selected in the system (Pulseaudio or other)?
From System>Preferences>Sound it is Autodetect.

---

### Post by zika on 2009-05-27
> **susancragin said:**
> I think you have to do this:
sudo apt-get purge pulseaudio
sudo apt-get install esound
Otherwise the configuration files remain.
beware:if You try to install esound You will loose ubuntu-desktop (probably with gdm) and You will have to install it again without GUI.

---

### Post by Soul-Sing on 2009-05-27
IMHO pulseaudio should not be completely removed, it can be disabled.
Removing pulseaudio removes a meta package,so an upgrade to an other version of ubuntu is (more) difficult.

---

### Post by zika on 2009-05-27
> **leoquant said:**
> IMHO pulseaudio should not be completely removed, it can be disabled.
Removing pulseaudio removes a meta package,so an upgrade to an other version of ubuntu is (more) difficult.+1
You can always disable it, for example, using sysv-rc-conf in Terminal. But I found it rewarding to give it some time and tune it properly ... (if You search Forum You will find that at one point I was disabling it and using ALSA but, now, after some time and certain improvement I am converted ... :)

---

