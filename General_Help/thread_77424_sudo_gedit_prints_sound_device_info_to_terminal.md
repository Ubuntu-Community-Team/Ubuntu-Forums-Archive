---
title: "sudo gedit prints sound device info to terminal?"
date: 2005-10-16
forum: General Help
---

### Post by veraction on 2005-10-16
Ok, I think it might have to do with me using [EasyUbuntu]("http://ubuntuforums.org/showthread.php?t=64629") to set up some things after installing breezy.

Anyways, here it is: ```
$ sudo gedit
Password:
- using device duplex
- using device duplex
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
```

it doesn't seem to do this with any other programs from what I've seen. And it won't print these messages if I'm just running gedit without sudo

Any ideas?

by the way, my sound is working fine (except for the fact I need to ```
killall -9 esd
``` anytime I reboot, or else no sound in some programs)

---

### Post by veraction on 2005-10-18
/bump

I found that these error/debug lines print to terminal when I just do a ```
gedit
``` too. I suppose I didn't notice cause ```
gedit &
``` doesn't print these lines.

Just noticed, the lines now are different, but similar:

```
~$ sudo gedit
- using device duplex
- using device duplex
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.

```

:confused: :confused:

---

### Post by veraction on 2005-10-19
/bump.

if anyone could just give me some hints as to where I'd look, (i.e. logfiles, etc)...

---

### Post by eggdeng on 2006-10-27
I have this issue too but no idea what to do about it. Unlike you, I didn't use easyubuntu. I get

- using device default
- using device default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

Maybe someone has filed it as a bug?

---

