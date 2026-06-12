---
title: "Sound inconvenience"
date: 2008-06-17
forum: General Help
---

### Post by cherva on 2008-06-17
Everything in linux is great. This is MY OS ! Thats why I like it :) But one thing is really the sound systems ! For an example when I play a game with wine ( configured to use alsa ) if someone call me on skype there is an error Problem with sound device, but if I start the call and then start the game everything is perfect. Same goes with watching a movie with mplayer. Mplayer uses pulse audio and when i watch a movie there is no sound if someone chat with me on skype. Every linux program uses a different sound system and there are tons of these inconveniences ... please advice me what to do.

---

### Post by cherva on 2008-06-18
So ... 22 hours and still no posts ? Interesting... no one has something to say about that?

---

### Post by Nepherte on 2008-06-18
There's a problem with pulseaudio/alsa when you use 2 sound applications simultaneously. The second one is refused access to the sound card. You can normally solve this by following the instructions in this topic: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by cherva on 2008-06-18
This guide didn't helped me ... now I have no sound in wine and if I set the microphone in skype to be to pulse i can listen to a song in amarok and call a person in skype, but there is much stuttering... if I set the mic to be to plughw:xxxxxxx the stuttering disapears and there is the same problem I can't listen to music and talk on skype ... so this guide didn't helped me... it just broke my alsa sound in wine...

---

### Post by Nepherte on 2008-06-19
> **cherva said:**
> This guide didn't helped me ... now I have no sound in wine and if I set the microphone in skype to be to pulse i can listen to a song in amarok and call a person in skype, but there is much stuttering... if I set the mic to be to plughw:xxxxxxx the stuttering disapears and there is the same problem I can't listen to music and talk on skype ... so this guide didn't helped me... it just broke my alsa sound in wine...
Did you actually read "Part C: Stuttering Audio Fix (bug #188226 and bug #190754)"?

No sound in wine sounds like a wine configuration problem, but since I don't use wine I can't help you with it.

---

### Post by cherva on 2008-06-19
I made part C ... Anyone knowing kow to make wine and skype play nice together ?

---

### Post by Nepherte on 2008-06-19
Are you running skype with wine or did I misunderstand this? If not, you can run skype native in linux without the need of wine. Otherwise you can ignore this post.

---

### Post by cherva on 2008-06-19
I run a native linux skype and I want to play games with wine while talking in skype :)

---

### Post by cherva on 2008-06-23
So, I guess at this time it is impossible to use skype ( linux version ) and wine together at the same time ...

---

