---
title: "Ubuntu 18.04 &amp; mpv player configurations"
date: 2018-08-09
forum: General Help
---

### Post by sardonic2 on 2018-08-09
Hi,
I have recently installed mpv with the Ubuntu software. I have noticed that once the song/movie is done the playback windows stays open.
[ATTACH=CONFIG]280692[/ATTACH]
Is there any ways to make it close automatically?
I have been unsuccessful with the mpv.conf and MPlayer.input so far.
Thank you for your help.

**mpv version:**
> mpv git-2018-07-22-45beb70 Copyright © 2000-2018 mpv/MPlayer/mplayer2 projects
 built on Thu Jul 26 15:04:40 UTC 2018
ffmpeg library versions:
   libavutil       56.18.102
   libavcodec      58.21.106
   libavformat     58.17.101
   libswscale      5.2.100
   libavfilter     7.26.100
   libswresample   3.2.100
ffmpeg version: git-2018-07-26-a8ce6fb

---

### Post by Holger_Gehrke on 2018-08-10
Since the versions of both mpv and the ffmpeg libraries you've got is a lot newer than the one I got from the Ubuntu repositories, I believe the one you got is probably a snap-package. Use 'snap list' in a terminal to verify.

The behaviour you're trying to achieve is default for the version in the repositories. On the command line the option '--idle=' followed by 'yes' (window stays open until you explicitly end the program), 'no' (if there's no file playing, close at once (probably not quite what you want;  closes immediately after start if no file is given on the command line)) or 'once' (idle window stays open after start(to enable d'n'd of media-files) but closes after playing a file) controls this. A line with 'idle=once' in ~/.config/mpv/mpv.conf should set the desired behaviour, but I do not know whether the snap version does (or even can) read that file. You could try to copy the .desktop-file for mpv into ~/.local/share/applications, edit it and change the exec-line in it to have an '--idle=once' option.

Holger

---

### Post by sardonic2 on 2018-08-10
> **~$ snap list**
Name                  Version    Rev   Tracking  Publisher  Notes
core                  16-2.34.3  5145  stable    canonical  core
gnome-3-26-1604       3.26.0     70    stable    canonical  -
gnome-calculator      3.28.2     180   stable/…  canonical  -
gnome-characters      3.28.2     103   stable/…  canonical  -
gnome-logs            3.28.2     37    stable/…  canonical  -
gnome-system-monitor  3.28.2     51    stable/…  canonical  -
gtk-common-themes     0.1        319   stable/…  canonical  -
matroska-tools        15.0.0-0   19    stable    jz         -



The: **~/.config/mpv/mpv.conf **I get permission denied and the mpv.conf is a blank page this is so confusing. I've tried to look after a "mpv file" with its configuration on it with no success!
It look like I have to edit my own configuration file and put it somewhere...?

---

### Post by mc4man on 2018-08-10
> **sardonic2 said:**
> Hi,
I have recently installed mpv with the Ubuntu software. I have noticed that once the song/movie is done the playback windows stays open.
[ATTACH=CONFIG]280692[/ATTACH]
Is there any ways to make it close automatically?
I have been unsuccessful with the mpv.conf and MPlayer.input so far.
Thank you for your help.

**mpv version:**
Simple, in ~/.config/mpv/mpv.conf add this section &  line (-create mpv.conf if not there, if  section is there than just the line
```

[pseudo-gui]
idle=once
```

Note that the ppa page does tell you this right near top
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

---

### Post by sardonic2 on 2018-08-10
> **mc4man said:**
> Simple, in ~/.config/mpv/mpv.conf add this section &  line (-create mpv.conf if not there, if  section is there than just the line
```

[pseudo-gui]
idle=once
```

Note that the ppa page does tell you this right near top
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)


Thank you very much! It worked.

---

### Post by mc4man on 2018-08-10
Keep in mind that your current/new mpv.conf just contains a profile section, ie. [pseudo-gui]
If you wanted to add at some point a general option or more you need to keep those at the top of the .conf, above any [profiles]

So for ex. if you wanted all your vids to open centered  you'd add this as such - 
```
geometry=50%:50%

[pseudo-gui]
idle=once
```

---

### Post by sardonic2 on 2018-08-10
> **mc4man said:**
> Keep in mind that your current/new mpv.conf just contains a profile section, ie. [pseudo-gui]
If you wanted to add at some point a general option or more you need to keep those at the top of the .conf, above any [profiles]

So for ex. if you wanted all your vids to open centered  you'd add this as such - 
```
geometry=50%:50%

[pseudo-gui]
idle=once
```


Excellent! But I have a question, how does mpv knows what to do beside the .conf I added. where does it stored the input and everything eles? Mpv's  folders don't show such thing.

---

### Post by mc4man on 2018-08-10
> **sardonic2 said:**
> Excellent! But I have a question, how does mpv knows what to do beside the .conf I added. where does it stored the input and everything eles? Mpv's  folders don't show such thing.
There are the default inputs, if one wished to set custom ones it's done thru a file, input.conf which is placed in the .config/mpv folder , see screens, I've only one input change myself.

You should, when mpv is open right click on the mpv launcher icon for some useful info I've provided. (only for unity and gnome-shell launchers, not sure about plank, definitely not docky..

---

### Post by #&amp;thj^% on 2018-08-10
> **mc4man said:**
> not sure about plank, definitely not docky..

It works for plank here.

---

### Post by sardonic2 on 2018-08-10
> **mc4man said:**
> There are the default inputs, if one wished to set custom ones it's done thru a file, input.conf which is placed in the .config/mpv folder , see screens, I've only one input change myself.

You should, when mpv is open right click on the mpv launcher icon for some useful info I've provided. (only for unity and gnome-shell launchers, not sure about plank, definitely not docky..

So every time that you want to customize something you have to create your own .conf and .input file to "overwrite" the default one?
Any way thanks you have been a great help!

---

### Post by mc4man on 2018-08-10
> **sardonic2 said:**
> So every time that you want to customize something you have to create your own .conf and .input file to "overwrite" the default one?
Any way thanks you have been a great help!
Not exactly. You create the .conf's once, then add or substract as needed/desired in the file.
Here I generally don't remove conf items I had found useful or interesting when not wanting to currently use, I just comment them out with a #

Ex. here's the top of my pretty simple mpv.conf, some things are commented, some not..

---

