---
title: "Serious Audio problem... HEEEELP PLEASE!!"
date: 2005-10-31
forum: General Help
---

### Post by ThirdWorld on 2005-10-31
all my problems started when i tried to install my plantronics USB headset. 

i follow a thread that show how to install the plantronics:

first i typed: 

echo "options snd_emu10k1 index=-2" | sudo tee -a /etc/modprobe.d/alsa-base

this was suposed to help my soundcard not to grab default 0

then the volume control disapear in my console. it ask me something about restarting something and I pressed cancel by mistake.  after that nothing works.


Now I have a serious audio problem. the system sound works sometimes, and sometimes it stops. However, application like XMMS always work after I configure it in preferences to use Alsa. When i open the multimedia system selector in system and test the audio output it said "failed to construct pipeline for alsa" 






wen i type this in console: cat /proc/asound/modules

it shows: 1 snd_emu10k1

it used to be: 0 snd_emu10k1

can somebody knows how i can return my sound card to default 0?


thanks

---

### Post by ThirdWorld on 2005-10-31
update:

Xmms works (streamtuner also works fine)

Amarok works

Totem works perfect, play dvds and everything

Xine works fine

real player dont work "cannot open audio device"

mplayer dont work


please help me this problem is driving me nuts...

---

### Post by ThirdWorld on 2005-10-31
HEEEELP!!! HEEELP!! 



sudo esd


ALSA lib confmisc.c:560: (snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948: (snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090: (snd_pcm_open_noupdate) Unknown PCM default



NOTE I HAVE TO SEPARATE : ( TO AVOID SMILIES

---

