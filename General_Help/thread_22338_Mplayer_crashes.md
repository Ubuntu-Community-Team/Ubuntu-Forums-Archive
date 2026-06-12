---
title: "Mplayer crashes"
date: 2005-03-27
forum: General Help
---

### Post by Nego on 2005-03-27
Well, I reinstalled haory, installed and aplied my ATI drivers, grabbed mplayer+mozilla plugin, and fonts for it of synaptic, got codecs and put them in their respective folders(got essenssial+all and put them in /usr/local/lib/codecs/ and /usr/lib/win32/), did smart upgrade with synaptic, and now mplayer crashed whenever I try to play any type of movie file. I did this b4 and mplayer worked just fine, but something seems to be wrong with it.  #-o

---

### Post by kahping on 2005-03-27
the forum's community may be able to help you out better (and faster, too) if you could provide a bit more details on the crash. 

any error messages in particular you could provide to help figure out the problem would be nice. ;-)

kahping

---

### Post by Nego on 2005-03-27
I don't get any error messages, when I try to play any type of movie file the screen on mplayer goes black and the UI part also goes black and Im forced to "force quit". Xine works fine, but I really prefer mplayer (for the mozilla plugin). When I try to play movies on firefox each movie will load to a certain amount (different for all files, but the same for each file) and stop.

---

### Post by RU63 on 2005-03-28
> MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
I get this message when trying to use MPLAYER. Also, when i try to use VLC and TOTEM I have video lag.  I was able to use MPLAYER last week but I had aweful video lag. And, a  about a week ago I was able to use totem with no sound lag.  So, I assume i have a sound issue.

HELP!!!!!

---

### Post by Nego on 2005-03-28
I went to prefrences and switched audio to OSS and that fixed mplayer crashing, but the mozilla plugin still will not work, each time I play a movie it will get to a certain amount and stop, each file will stop at a different amount, but the same file stops at the same amount all the time.

---

