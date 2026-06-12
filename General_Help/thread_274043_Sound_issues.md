---
title: "Sound issues"
date: 2006-10-09
forum: General Help
---

### Post by wogdog on 2006-10-09
I'm running Ubuntu 6.06 as a MythTV box and it was running wonderfully, that is until I moved from one desk to another.  Everything is plugged in just fine but my sound is not working properly.  I can hear the startup and shutdown sounds, but that's ALL I can hear.  If I play a video locally, I get no sound, if I attempt to watch TV through MythTV, I get no sound.

Everything appears to be fine in the logs.

```
mythtv@alfalfa:/etc/apt$ lspci | grep audio
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

```

```
mythtv@alfalfa:/etc/apt$ dmesg | grep audio | more
[17179588.664000] tveeprom: audio processor = CX25843 (type = 25)
[17179594.884000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)

```

Has this happened to anyone else?  Any assitance would be appreciated. 

wogdog

[edit: corrected spelling error]

---

### Post by rootchick on 2006-10-13
I've been having the same issue over the last few days.  Did you find a solution?

---

### Post by robcarr2 on 2006-10-13
I cant really help you but try looking in the programs prefence / option page, you can usually select which sound device to use from the program.

I know my answer is probably of no help, but thought I would contribute what I would of tried if it was happening to me.

---

