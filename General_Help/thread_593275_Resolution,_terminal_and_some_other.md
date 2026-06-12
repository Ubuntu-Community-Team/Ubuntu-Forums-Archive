---
title: "Resolution, terminal and some other ?"
date: 2007-10-27
forum: General Help
---

### Post by Simple512 on 2007-10-27
Hello, not sure if anyone remembers me I started a thread on prep for installing Ubuntu. Well, im proud to say im posting this from Ubuntu and not windows. 

Anyway on to some issues im having ( i just installed it now and its running fine im logged into aim through gaim ! )

But, my native resolution on my computer is 1024x1280 (maybe its the reverse of that i forget) LCD and i like that resolution alot. But when i go under system, screen resolution the highest is 1024x768 and i dont like how it looks on my monitor. How do i change this. I read some posts on this issue and people were talking about typing in some oddddd code in a terminal. How do i do this ?

Also am i supposed to do anything to the swap drive that i formatted when i installed ubuntu or can i just leave it be ?

Thanks guys you are very helpful i know you will help me :)

---

### Post by taurus on 2007-10-27
Add the resolution you want to use in /etc/X11/xorg.conf.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
The system will use your swap partition when it needs to so don't worry about it.

---

### Post by Simple512 on 2007-10-27
ok thanks man i will try that

---

### Post by Simple512 on 2007-10-27
Is it ok if it gave me this error,

```
 gksudo gedit /etc/X11/xorg.conf
(gedit:6844): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```




And what exactly do i insert in the file it opened ? I seen the display resolutions but do i put it before after ? And can someone give me the syntax for it too ? Thanks guys

---

### Post by Simple512 on 2007-10-27
ok under where it listed the resolutions, i added "1280x1024" to each display now it should work ? but when i go to resolution it isnt listed there.

---

### Post by Simple512 on 2007-10-27
ok thanks anyway, i figured it out ty whoever helped me ;)

---

