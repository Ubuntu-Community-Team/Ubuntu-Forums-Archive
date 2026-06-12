---
title: "Using FFMPEG to convert AVIs (changing resolution, bitrate)"
date: 2007-08-06
forum: General Help
---

### Post by FleetAdmiral74 on 2007-08-06
So I have an avi file. I want to convert it to 

```
AVI
320 x 240
30 frames a second
Bitrate can be adjusted.  Default usually 512 kbps
Audio 128 kbps
```

The AVI file has these properties right now (got from right clicking and using the aud/vid tab
```

624x352
Codec: Xvid MPEG-4
24 framers per second
Bitrate N/A (is this right?)

Audio 132 kbps
mpeg-1 layer 3
```

Hope this is pretty easy :)

I read a bit of the documentation, but it was kinda...huge. I am still reading, but I figure this would get a more timely response then me using trial and error.

---

### Post by distroman on 2007-08-07
```
mencoder input.avi -o output.avi -oac mp3lame -lameopts abr:br=128:vol=9 -ovc xvid -xvidencopts pass=2:bitrate=3000 -vf scale=320:240 -ofps 30
```
I think you can get it done with this or close anyway :)

---

### Post by FleetAdmiral74 on 2007-08-07
Alrighty, I will give it a try and update in the morning.

EDIT: It is working...getting a whole lot of ```

1 duplicate frame(s)!
mpg123: Can't rewind stream by 25 bits!: 110min 402mb  A-V:0.031 [288:121]
P
```

However. I will see if it will work in the end with a playable file.

---

### Post by FleetAdmiral74 on 2007-08-07
> **FleetAdmiral74 said:**
> Alrighty, I will give it a try and update in the morning.

EDIT: It is working...getting a whole lot of ```

1 duplicate frame(s)!
mpg123: Can't rewind stream by 25 bits!: 110min 402mb  A-V:0.031 [288:121]
P
```

However. I will see if it will work in the end with a playable file.

Double edit: Well, the audio is static, and it only went to 4:50. The last output was ```
1 duplicate frame(s)!
Pos: 287.7s   7494f ( 3%) 30.83fps Trem: 111min 403mb  A-V:0.029 [286:121]
ed@ed-desktop:~$ 

```

And the command I used was ```
 mencoder /media/hda1/home/ed/luckymovie/lucky.avi -o /media/hda1/home/ed/luckymovie.avi -oac mp3lame -lameopts abr:br=128:vol=9 -ovc xvid -xvidencopts pass=2:bitrate=3000 -vf scale=320:240 -ofps 30

```

NOTHER EDIT: I found out quote != edit

---

### Post by distroman on 2007-08-07
The “a whole lot of” comes when you try to change the frame rate. 
```
1 duplicate frame(s)!
Pos:  58.4s   1465f (99%) 30.98fps Trem:   0min   6mb  A-V:0.005 [784:126]
```
That's what I get.

---

### Post by FleetAdmiral74 on 2007-08-07
> **distroman said:**
> The “a whole lot of” comes when you try to change the frame rate. 
```
1 duplicate frame(s)!
Pos:  58.4s   1465f (99%) 30.98fps Trem:   0min   6mb  A-V:0.005 [784:126]
```
That's what I get.

lol, did you mention something I can try and I am just missing it? Or were you just informing me ;)

Anyway, progress is progress, and I thank you for your time.

---

### Post by distroman on 2007-08-07
Did you need something new to try? It didn't work?

---

### Post by FleetAdmiral74 on 2007-08-07
Hmm, obviously some miscommunication. My last feedback was "the audio is static, and it only went to 4:50", this was after trying the first (and only terminal command) I am aware of currently for this task. 

And then you told me the frame rate was the reason I was getting the terminal output. And then....I just sat here confused, waiting for more guidance :popcorn:

I am not sure what to do...maybe you were suggesting something obvious, but I might have missed it. Or you misread my whole double post/edit thing, got kinda messy, and you could have missed my last update.

Sorry about this.

---

