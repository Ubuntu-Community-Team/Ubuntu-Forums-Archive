---
title: "Boot Scripts"
date: 2008-07-01
forum: General Help
---

### Post by moosehadley on 2008-07-01
Does anyone know how to make a boot script that would play music while the system starts? (much like Sabayon)

I was thinking that it could just do:

mplayer "/uru.ogg"

But I dont know how to program this

---

### Post by kuja on 2008-07-01
Well, you could create a script in /etc/init.d/

- Mark it executable (sudo chmod +x /path/to/somescript.sh)
- Include the line "#!/bin/sh" at the top of the file
- Second line will be the music player line
- Rather than using update-rc.d, it might be better to manually set up the symlink so it can play earlier (not sure if alsa will cope though), try this, assuming it's in /etc/init.d and named somescript.sh (which is a pretty crappy name, think of a better one :))
```
sudo ln -sf /etc/init.d/somescript.sh /etc/rc{2..5}.d/S02somescript.sh
```

Well ... give that a try and let me know how it goes.

---

### Post by moosehadley on 2008-07-11
Works great, with one small problem.


The rest of the boot process pauses while it waits for mplayer to finish.

I wanted the music to play while it boots, not before.

Any solutions?

---

### Post by kuja on 2008-07-12
Try putting a "&" at the end of the command, which should make it run in the background.

---

### Post by moosehadley on 2008-07-12
Works great, thank you so much for this!

To make it stop playing when the GUI starts to load, I added 

```
killall mplayer
```

to rc.local, its messy, but it works.

Thank you once more!

---

### Post by dracayr on 2008-07-12
that's a damn good Idea :)

but is there a way to make it start earlier?

dracayr

---

### Post by kuja on 2008-07-12
Getting it to start earlier would probably involve adding it to the init image or something, I would presume. I'm not 100% on how to go about that.

---

### Post by fitzefitzefatze on 2009-08-24
I know this is an old thread but it's my current problem. I followed the advises but in my case I don't need to kill mplayer because it stops automagically after finishing booting and starting the GUI. 

My script: /etc/init.d/playMusicOnBoot.sh

```

#!/bin/sh
mplayer /pathToSong/song.mp3&

```

then I did:

```

sudo ln -sf /etc/init.d/playMusicOnBoot.sh /etc/rc2.d/S02playMusicOnBoot.sh
sudo ln -sf /etc/init.d/playMusicOnBoot.sh /etc/rc3.d/S02playMusicOnBoot.sh
sudo ln -sf /etc/init.d/playMusicOnBoot.sh /etc/rc4.d/S02playMusicOnBoot.sh
sudo ln -sf /etc/init.d/playMusicOnBoot.sh /etc/rc5.d/S02playMusicOnBoot.sh
sudo ln -sf /etc/init.d/playMusicOnBoot.sh /etc/rcS.d/S02playMusicOnBoot.sh

```

So my questions are:
1) why does it stop? - I guess perhaps because a gui starts and mplayer has also a gui (although typeing the command mplayer /.../song.mp3 no gui starts) or the rc.local script finishes the command by exit 0? But honestly I have no clue.

2) how can i convince Ubuntu to play on?

3) [quote="dracayr"]
but is there a way to make it start earlier?
[/quote]

Tanks for your help.

PS (edit): 
I am using Ubuntu 9.04

---

