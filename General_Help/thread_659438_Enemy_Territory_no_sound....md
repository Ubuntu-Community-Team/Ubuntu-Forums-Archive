---
title: "Enemy Territory no sound..."
date: 2008-01-05
forum: General Help
---

### Post by Moonfrost on 2008-01-05
Hi all, I just installed Enemy Territory for Linux and it runs perfectly except that I get no sound...I tried some of the solutions on this forum and others but nothing works!...

This is what I get when I run it from terminal in the sound intialization:

```
------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp

```

---

### Post by ~LoKe on 2008-01-05
Try this:
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

---

### Post by Moonfrost on 2008-01-06
> **~LoKe said:**
> Try this:
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

Ok, I tried that and I get permission denied, I tried it with sudo and still get permission denied and then I did su to become super user, I became su and then tried again and nothing happens...

---

### Post by ~LoKe on 2008-01-06
> **Moonfrost said:**
> I became su and then tried again and nothing happens...

It's not supposed to output anything.  Did you try checking if sound works?

---

### Post by Moonfrost on 2008-01-06
> **~LoKe said:**
> It's not supposed to output anything.  Did you try checking if sound works?

I tried now and sound still doesn't work at all...

---

### Post by CLANWIRE on 2008-01-06
is it a onboard sound card?

---

### Post by bharadwaj on 2008-01-06
et-sdl-sound (Run ET With ALSA)

There is an alpha hack which is around that makes Return To Castle Wolfenstein Enemy Territory play with ALSA by replacing standard sound system functions in runtime as aoss won't work for ET. I found this necessary when wanting to run TeamSpeak 2.XX at the same time.

It's located at [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)

Simply download the latest tarball [http://nullkey.ath.cx/~stuff/et-sdl-...l-sound.tar.gz](http://nullkey.ath.cx/~stuff/et-sdl-...l-sound.tar.gz)

1. Extract

2. Copy et-sdl-sound.so file to /opt/enemy-territory/

3. Open your favourite text editor and add the following lines and save as et_sdl_sound.sh:
#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /opt/enemy-territory/
LD_PRELOAD="/opt/enemy-territory/et-sdl-sound.so" ./et.x86 $*

4. chmod +x et_sdl_sound.sh

5. ./et_sdl_sound.sh

Note if you want to hook this up to XQF you need to tell XQF that the "Command Line" is "/opt/enemy-territory/et_sdl_sound.sh" and the "Working Directory" is "/opt/enemy-territory/"

---

### Post by Moonfrost on 2008-01-06
> **CLANWIRE said:**
> is it a onboard sound card?

Yeah, it's a Realtek HD onboard audio if I'm not mistaken

---

### Post by Moonfrost on 2008-01-06
> **bharadwaj said:**
> et-sdl-sound (Run ET With ALSA)

There is an alpha hack which is around that makes Return To Castle Wolfenstein Enemy Territory play with ALSA by replacing standard sound system functions in runtime as aoss won't work for ET. I found this necessary when wanting to run TeamSpeak 2.XX at the same time.

It's located at [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)

Simply download the latest tarball [http://nullkey.ath.cx/~stuff/et-sdl-...l-sound.tar.gz](http://nullkey.ath.cx/~stuff/et-sdl-...l-sound.tar.gz)

1. Extract

2. Copy et-sdl-sound.so file to /opt/enemy-territory/

3. Open your favourite text editor and add the following lines and save as et_sdl_sound.sh:
#!/bin/bash
export ETSDL_SDL_LIB="libSDL.so"
export SDL_AUDIODRIVER="alsa"
cd /opt/enemy-territory/
LD_PRELOAD="/opt/enemy-territory/et-sdl-sound.so" ./et.x86 $*

4. chmod +x et_sdl_sound.sh

5. ./et_sdl_sound.sh

Note if you want to hook this up to XQF you need to tell XQF that the "Command Line" is "/opt/enemy-territory/et_sdl_sound.sh" and the "Working Directory" is "/opt/enemy-territory/"


Tried your method but it doesn't seem to work, ./opt/enemy-territory/ doesn't exist on my system, I also tried my actual installation directory /usr/local/games/enemy-territory but that still doesn't work...tried making the text file with the exact commands you posted but it tells me "no such file or directory", then I tried the making a text file with the same command but changing "cd/opt/enemy-territory" to "/usr/local/games/enemy-territory and still get the same thing.

I also moved the sh file I created to enemy territory's installation directory and it still doesn't find the file at all...the only method that works seems to be the one on the first link you posted but I would have to start the game through the command line every single time...

---

### Post by FriedChips on 2008-01-08
[http://ubuntuforums.org/showthread.php?t=362231&highlight=enemy+territory+sound](http://ubuntuforums.org/showthread.php?t=362231&highlight=enemy+territory+sound)
check there for help

---

### Post by Rytron on 2008-03-07
Hi Moonfrost,
Try this

```
sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et
```

---

### Post by grossaffe on 2008-03-15
> **Rytron said:**
> Hi Moonfrost,
Try this

```
sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et
```

Do you know how i would code a script to do this every time I ran the game?

---

