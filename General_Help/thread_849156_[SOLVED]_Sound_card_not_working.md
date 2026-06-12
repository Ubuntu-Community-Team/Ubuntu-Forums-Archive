---
title: "[SOLVED] Sound card not working"
date: 2008-07-04
forum: General Help
---

### Post by kempy1000 on 2008-07-04
Hello
On my headless server i run mpd and control it from my laptop using sonata. However i decided to remove all the packages from my server that i thought were useless to free some space (gnome etc) it all went well and i freed a great deal of space. 
But now when i try to connect to mpd it connects but will not play anything.
I started the daemon using the script i use to start it a boot and the output from it was this:

```


ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default


```

I presume i have removed a package that has now caused the problem.

Thanks
Chris

---

### Post by pedro_orange on 2008-07-04
Hi kempy1000,

From the looks of it your system cannot recongise your sound card or something. What happens when you type the following into terminal:

```
aplay -l
```

This page may help you out: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If your card is listed, then I guess you removed an alsa package by mistake. Which would probably just mean a reinstall of the given package. (I would guess it's alsa-base or something similar)

---

### Post by kempy1000 on 2008-07-04
Hi
Thanks for reply

The output from aplay -l is:

```

chris@chimera:~$ aplay -l
aplay: device_list:205: no soundcards found...

```

I will look at the documentation as soon as i can.

Thanks
Chris

---

### Post by kempy1000 on 2008-07-04
I cant access the web address supplied it keeps timing out.

So my problem still persists.

Thanks
Chris

---

### Post by kempy1000 on 2008-07-04
Just been trying a few things and i found that lspci -v shows my sound card:

```


00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: ASRock Incorporation K7VT6 motherboard
	Flags: medium devsel, IRQ 5
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>


```

Chris

---

### Post by kempy1000 on 2008-07-05
Fixed Using this:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Thanks Chris

---

### Post by pedro_orange on 2008-07-07
Sorry kempy I was away for the weekend!

However, I am glad you fixed your problem!

Pedro

---

