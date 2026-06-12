---
title: "Alsa"
date: 2007-11-18
forum: General Help
---

### Post by grahambo2005 on 2007-11-18
Hi All

I am fairly new to ubuntu only been using it a couple of weeks

I'm having an Issue with the sound though

I currently am using ESD and everything works fine, I can here system beeps, listen to music and watch videos on youtube all with sound.

But i have recently installed Beyond the Red Line (a game) and I cant hear any sound.

here is whats coming up when I attempt to run this from the terminal

> graham@graham-desktop:~/btrl_demo$ sudo sh btrl_demo
ALSA lib pcm.c:2105: (snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
open /dev/[sound/]dsp: Device or resource busy


So I had a quick read up about ALSA but when I attempted to set ALSA as my default sound output i got an error when I clicked test

> audiotsr wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resouce busy or not available.

So now I'm not sure where to go next.
I have my default Audio mixer set to Realtek ACL883 (OSS Mixer)

I am using 7.10

any suggestions?

Cheers

Graham

---

### Post by grahambo2005 on 2007-11-18
Also I have 2 hard drives

I have ubuntu installed on one and the other has media etc, everytime I want to access the media drive I have to mount it. its a real annoyance. is there anyway I can persitantly mount this drive?

---

### Post by grahambo2005 on 2007-11-18
ok guys

havnt gotten much feedback on this post

but ive got more info which may make someone oming up with a solution for me easier

the file *libasound_module_pcm_pulse.so* is missing

what do I need to install so thats its there

in that diretory I have to following 

libasound_module_ctl_bluetooth.la  
libasound_module_pcm_bluetooth.la
libasound_module_ctl_bluetooth.so  
libasound_module_pcm_bluetooth.so

PLEASE HELP

Graham

---

### Post by grahambo2005 on 2007-11-18
Ok I've gotten the above fixed...

now I'm getting this!

[I]ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
open /dev/[sound/]dsp: Device or resource busy
(null): "DirectSound could not be initialized.  If you are running any applications playing sound in the background, you should stop them before continuing."[/I]

Where do I go from here?

Graham

---

