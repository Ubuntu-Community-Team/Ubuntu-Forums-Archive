---
title: "Sound problems"
date: 2005-07-30
forum: General Help
---

### Post by twermund on 2005-07-30
Hey, I just put Ubuntu on my old Windows box, and I'm very happy with it. However, I've been having some sound problems. At first, although most applications couldn't use sound, some could (the normal Ubuntu sounds, VLC, and Gaim could use sound). I listened to a few mp3's on VLC, all of which had been used by a friend also running Ubuntu. They all worked. However, I opened one particular mp3, and it didn't play sound like it did for my friend. Now, none of the mp3's I played worked. Now, only Gaim and Ubuntu can play sounds. I'm pretty sure it wasn't a virus, since it was OK for my friend who played it. Does anyone know what's up?

By the way, here are a couple of error messages from programs that wouldn't run sound:

1. Warning: Couldn't set 22050 Hz 16-bit audio - Reason: No available audio device
Sound and Music will be disabled

2. There was an error initializing the audio i/o layer. You will not be able to play or record audio.

Error: Host error.

---

### Post by pr00f 0f d3f on 2005-07-30
is alsa running correctly? check to see if you get an error for alsa on bootup. also, run alsamixer in the console and see what it says your sound device is. your applications might also need to be set to use the alsa sound driver.

---

### Post by DeathOnJuice on 2005-07-31
[QUOTE=pr00f 0f d3f]is alsa running correctly? check to see if you get an error for alsa on bootup. also, run alsamixer in the console and see what it says your sound device is. your applications might also need to be set to use the alsa sound driver.[/QUOTE]
 This is the same person, but I was on a friend's account.

Anyway, alsa seems to be running correctly. My sound card is Intel 82801BA-ICH2 and my chip is Analog Devices AD1885. After I posted this topic, I shut down my computer for a few hours. When I turned it back on, VLC worked again. Still, could you help me troubleshoot my other problem (where most applications can't use sound)? How would I set them to use the alsa sound driver?

---

### Post by DeathOnJuice on 2005-08-01
I'm new to these forums, so sorry if I'm not supposed to do this, but this post is to bring this topic back to the top of the list.

---

