---
title: "MPlayer &amp; AC3"
date: 2005-04-20
forum: General Help
---

### Post by tspec on 2005-04-20
I was wondering how to get a file with AC3 sound to work in MPlayer? Everything else seems to be working in it... divx, xvid, mp3 sound etc etc but the moment I play a file that contains AC3 sound I get the following error:

--------------------------
MPlayer interrupted by signal 11 in module: decode_audio

-MPlayer crashed by bad usage of CPU/FPU/RAM.
Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.

-MPlayer crashed. This shouldn't happen.
It can be a bug in the MPlayer code _or_ in your drivers _or_ in your gcc version. If you think it's MPlayers fault, please read /DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and won't help unless you provide this information when reporting a possible bug.
--------------------------

Note: I haven't looked into these bugreport files yet because i believe it's just an ac3 install prob. Probably not a bug with the player (i could be wrong though, i am pretty new to linux and mplayer)

AC3 sound does appear to be installed because it's works in totem and xine, only reason im not using them to play the xvids is that running them in those players plays the file looking completely messed up but xvids running in mplayer work fine (assuming they're not encoded with AC3 sound). I tried changing a few of the audio options in MPlayer but that didn't seem to help. Is there some kind of AC3 plugin for MPlayer that I could be missing? I have the standard codecs installed like w32codecs etc.

I've glanced over google and various guides but people getting this error tend to be having trouble getting mplayer to run at all whereas im just having trouble with one codec.

If theres any more information you guys need to help solve the problem let me know.

---

### Post by skoal on 2005-04-20
It's been awhile since I've done this because a cap blew on my old receiver, but here's how I piped AC3 to my external decoder:

gmplayer -ao alsa1x -ac hwac3 -af-adv force=3

* some syntax may have changed with a newer version and there's no way for me to test it at present.

Use '-ac a52' (for software AC3) if you don't have an external decoder like mine.  The '-af-adv force=3' option tells mplayer to quit sending me 'missing audio format' dialogs.  The GUI settings manager doesn't work quite as well in my experience.

---

### Post by tiger338 on 2005-04-25
Thank you ..

Your tip works for me..

I did not know how to specify alsa channel to play AC3 formatted movie file.

Here is what I did for Hoary 5.04

1. Disabled esd daemon. 
    System -> Preferences -> Sound
    Uncheck "Enable sound server startup"

2. Restart gnome. (Ctrl + Alt + BackSpace)

3. Run the following command.
    mplayer -ao alsa -ac hwac3 -af-adv force=3 [movie file name]

It work without error but I can not make movie screen zoom.

---

### Post by chronos on 2006-05-05
Old thread, but... any new suggestions? I have the exact same problem. I've tried what skoal said and also changing the codecs in the gui settings, but it always crashes the same way.

---

### Post by Hubris2 on 2006-11-13
deleted

---

