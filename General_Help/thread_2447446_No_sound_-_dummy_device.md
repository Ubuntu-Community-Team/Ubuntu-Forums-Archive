---
title: "No sound - dummy device"
date: 2020-07-19
forum: General Help
---

### Post by mickee384 on 2020-07-19
Hi all. I need some help in fixing the issue with no sound on my ubuntu 20.04installation. What happened was I installed the Unity DE and switched to lightdm. I ran that for a bit and decided to switch back to ubuntu gnome. When I enabled GDM3, there was a message about sound. I'm sorry, I should have paid more attention, but it was after loading up ubuntu again, I had no sound. It shows a dummy device in the output in sound settings. I checked and the sound card shows up in the aplay -l 

I am really hoping someone will help me fix the issue I caused. :confused: If you need specific outputs like listings etc, let me know and I will provide them. I'm really not very good at sound and hardware when it comes to Linux. Anyhow, any help will be much appreciated!

---

### Post by mickee384 on 2020-07-19
ok, so ran this: ```
pulseaudio -k && sudo alsa force-reload
``` - now the card show up in the sound settings! But alas, still no actual sound

---

### Post by mickee384 on 2020-07-19
crapola! Rebooted and now back to dummy output. Created /etc/asound.conf as follows: 
```
defaults.pcm.card 0
defaults.pcm.device 0
```

I believe that is the card and device

---

### Post by mickee384 on 2020-07-19
while creating that file I received the following error in terminal (sudo nautilus):
```
ALSA lib confmisc.c:767:(parse_card) cannot find card '0'
ALSA lib conf.c:4693:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4693:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1246:(snd_func_refer) error evaluating name
ALSA lib conf.c:4693:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5181:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2642:(snd_pcm_open_noupdate) Unknown PCM default
```

and doing aplay -l shows no soundcards found

---

### Post by mickee384 on 2020-07-19
renamed /etc/asound.conf to .old to take that out of the equation. This time the alsa error is not outputted.

---

### Post by mickee384 on 2020-07-19
ran pulseaudio -k && sudo alsa force-reload again.
```
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

---

### Post by mickee384 on 2020-07-19
did the following:

sudo gedit /etc/modprobe.d/alsa-base.conf

added the following at end of file
```
options snd-hda-intel dmic_detect=0
```

rebooted and still no difference

---

### Post by mickee384 on 2020-07-19
no sound card shows in ```
sudo lspci
```

---

### Post by mickee384 on 2020-07-19
maybe this thread needs to move to hardware?

---

### Post by mickee384 on 2020-07-19
a side note. In the American Megatrends BIOS - there are very few settings and nothing under Advanced. This looks weird to me. Is there a way to enable all the settings?

---

### Post by mickee384 on 2020-07-19
sudo lspci shows the card in the output now:
```
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
```

and just like that - gone again!

---

### Post by mickee384 on 2020-07-20
its actually Dummy Output

---

### Post by mickee384 on 2020-07-28
turns out I had to do a complete shutdown/restart rather than just rebooting

---

