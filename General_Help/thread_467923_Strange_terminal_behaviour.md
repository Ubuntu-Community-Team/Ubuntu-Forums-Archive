---
title: "Strange terminal behaviour"
date: 2007-06-08
forum: General Help
---

### Post by PaulFXH on 2007-06-08
I just upgraded to Feisty Fawn a few days ago and, in general, it's working fine.
However, my terminal is behaving strangely when I use it to open a text editor. So, if I type:
```
sudo gedit /boot/grub/menu.lst
```
I get this before the editor opens.
> ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory

and about 15 more similar lines (I couldn't include them here as the permitted number of images in this message was exceeded).

Now, I did try some enhancements of my terminal yesterday using [this]("http://ubuntuforums.org/showthread.php?t=202249") and [this]("http://www.lifehacker.com/software/featured-linux-download/customizable-terminal-sessions-with-tilda-264327.php").
Does anybody know why I'm getting this stuff showing up in terminal?

---

