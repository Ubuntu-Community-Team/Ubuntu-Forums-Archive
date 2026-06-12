---
title: "Audio programs don't play nicely - Amarok won't play"
date: 2007-04-30
forum: General Help
---

### Post by Area51mafia on 2007-04-30
Hello.

Just recently upgraded to Feisty.

Before the upgrade I could have 2 programs playing Audio at the same time and everything would be just fine. Now, however, if I try to have Flash play a video while listening to some music, Amarok won't play anything, instead it'll give a Xine error that the device is busy. If I load Flash while Amarok is playing, both will play at the same time just fine. But if I pause Amarok, reload the Flash plugin, start the video going, then attempt to unpause Amarok it will error out.

I've read that this could be due to something with ALSA locking the sound card (which Flash uses), and Amarok being set to Autodetect, choosing OSS, and meeting a locked card. I've set Amarok to use the ALSA driver too, which has the exact same thing happen to it. Then a friend mentioned to me that it could have something to do with dmix and software, and not hardware, based mixing. I read that the new version of ALSA doesn't have a need for dmix anymore (or something like that), and it's not included any more. Could that have something to do with my problem?

If you need any more information, feel free to ask.Any help is greatly appreciated.

Thanks.

---

### Post by Area51mafia on 2007-05-01
Does anybody know what could be causing this? or how I could possibly fix it? It's becoming really annoying.

---

### Post by Area51mafia on 2007-05-03
My friend suggested that I try setting Amarok to ESD as its driver. That seemed to work, but ended up not fixing the problem. I tested it by setting it to ESD, restarting Amarok, pausing, opening a youtube video, then attempting to play Amarok. It acts like it's playing (the analyzer pulses and it increases in time, although at a faster rate) but no sound comes out.

Anybody?

---

### Post by ender542 on 2007-06-18
I found that running "amarok music.mp3" (where music.mp3 is a music file) worked while just calling "amarok" did not.

---

