---
title: "[SOLVED] no alsa - no sound card configured"
date: 2007-12-25
forum: General Help
---

### Post by Tyke91 on 2007-12-25
I've been using ubuntu for a year now and i've only ever had this problem once before... but i've lost my original post so I guess i have to ask again :(

how can you set up an undetected sound card to run with ubuntu? I'm using a dell inspiron 1720 with a High Definition Audio 2.0 sound card and Gutsy.

---

### Post by danwood76 on 2007-12-25
Normally to install sound you just compile and install alsa.
Quite often the newest cards arent supported by the alsa version in the repositories.

If that doesnt work you may need to have a look around the alsa bug system as quite often there are solutions there.

regards,
Danny

---

### Post by Tyke91 on 2007-12-25
hmm, i tried the guide on this page [https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29")
and got all the way to finishing compiling/installing alsa drivers from source, but when i go back to tell it to do sudo modprobe snd-intel8x0 , it gives me an error message

by the way, the sound device is an intel 82801H HD audio controller

i also tried compiling 8x0m, but it didn't work either.

---

### Post by Tyke91 on 2007-12-25
so, I've discovered that something can make a sound inside my computer... every once in a while it will do a system beep, so at least I know that something can control sound inside of it.

other than that, I'm stumped at what to do next.

---

### Post by Casual Fan on 2007-12-25
No idea if this will be useful for you:

 [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Good luck!

---

### Post by Tyke91 on 2007-12-26
lol :) it is the same guide as the wiki. 

I will keep trying though, it would be nice if i could find someone who has had the same problem.

do you guys think a full reinstall of ubuntu would help?

---

### Post by Dr.Gringo on 2007-12-26
I have the same problem that you do and i believe my sound card is the same or very similar to yours. Im running ubuntu on a HP Pavillion dv6000 laptop with no sound I hope we can get some help ive been trying different instructions to no avail. Im leaving tomorrow on a trip and it would be nice if i could get the sound working.

Some more Data in hopes of HELP:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by danwood76 on 2007-12-26
I have the same card. the actual alsa driver is the snd-hda-intel.
try doing sudo modprobe snd-hda-intel. if you get an error can you post it please?

regards,
Danny

---

### Post by Tyke91 on 2007-12-26
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

i'm going to try the whole process again

---

### Post by Tyke91 on 2007-12-26
so, i did the whole process over again and did ```
sudo modprobe snd-hda-intel
```

this time i got no error message, but I dont have any sound either, aplay -l doesn't find any soundcards.

---

### Post by Tyke91 on 2007-12-26
what is the output supposed to be for that command anyway? is there supposed to be output? should I be getting sound directly after doing that command?

---

### Post by danwood76 on 2007-12-26
if it loaded the module then it will give you no output.
have a look in hardware information to see if your card is listed and if its loaded the hda-intel driver. 
If the driver has loaded then you may need to edit the sound options, you can specify the config of your sound card when it loads by editing a config file, I forget which file and im not at my PC right now. I think its documented in the alsa install instructions anyway.

regards,
Danny

---

### Post by Tyke91 on 2007-12-26
that's weird... back when i posted it ran and gave no output (assuming it works). now when I load the module (after a reboot), it's giving me that same error message.

---

### Post by danwood76 on 2007-12-26
I just had a look at that wiki guide you followed, which method of compiling the drivers are you using?
if you choose to use the drivers from the alsa project (which I recommend) you should get the latest version of the driver from the alsa site, 1.0.15 as opposed to the 1.0.12 that is on the wiki.

you also need to make sure you specify snd-hda-intel when you compile to make sure it builds the correct modules.

sorry I cant help further, I have never experianced errors like that, I can only assume that it is due to compiling the wrong module.

regards,
Danny

---

### Post by Tyke91 on 2007-12-26
I had used the apt method of getting the latest drivers... ill try doing it your way when I get to my computer.


thx for all the help :guitar:

---

### Post by danwood76 on 2007-12-26
If you get any problems whilst compiling I will be sure to help. Its no problem.

Good luck!
Danny

---

### Post by Tyke91 on 2007-12-26
no problems compiling, though I did accidentally compile EVERY alsa driver by pressing enter too fast... i hope it didn't affect the outcome, besides cost me a bit more system memory.

I was told that the drivers compiled and installed successfully and to watch out, because alsa is muted by default. but sudo modprobe snd-intel-hda still doesn't work :(


was it because of all the drivers, or did something go wrong? I did use 15 instead of 12, as you suggested.

---

### Post by danwood76 on 2007-12-26
Whenever ive compiled the alsa drivers I compiled them all and just loaded the needed one, so that wouldnt be your problem.

could you tell me the ourput of lspci -v | grep 'Audio'

regards,
Danny

---

### Post by Tyke91 on 2007-12-26
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by Tyke91 on 2007-12-26
THX DANNY! :guitar:


all that was needed was a reset. thanks for the help and merry christmas (what's left of it)

---

### Post by danwood76 on 2007-12-27
No problem, glad to help.
Merry Christmas to you!

Add [SOLVED] to the start of the title so that others can read and help themselves ;)

---

