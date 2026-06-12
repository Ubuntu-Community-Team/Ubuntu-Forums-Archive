---
title: "green noise generator, trying to download but it hangs"
date: 2023-12-27
forum: General Help
---

### Post by Skaperen on 2023-12-27
i want to get a sound generator that generates green noise (as opposed to white noise, etc).  i could not find anything in the main repository but duckduckgo found "blanket" that seemed like it would do it.  trying to download it just hangs when doing the update.  maybe some other program could be used?  it is important that this works even when the internet is down so this rules out videos on YouTube. any suggestions?

---

### Post by Holger_Gehrke on 2023-12-27
Reading the github for blanket, there's both a PPA ([https://launchpad.net/~apandada1/+archive/ubuntu/blanket](https://launchpad.net/~apandada1/+archive/ubuntu/blanket)) and a flathub download ([https://flathub.org/apps/details/com.rafaelmardojai.Blanket](https://flathub.org/apps/details/com.rafaelmardojai.Blanket)). Looking further, it might be possible to use sox to generate the noise you want. [This]("https://unreasonable.org/white_noise_generator_with_sox_for_Linux") article describes how to use sox to generate pink noise - which seems somewhat related - and [this]("https://www.johndcook.com/blog/2016/04/27/how-to-create-green-noise-in-python/") article describes the spectrum of green noise and gives python code to generate a wav file full of it.

Holger

---

### Post by ActionParsnip on 2023-12-27
Could just play a YouTube video of the sound in your browser....? Is this not easier or is this a command line only system?

---

### Post by Dennis N on 2023-12-27
I have **Blanket** installed as a Flatpak. It works fine.

---

### Post by MAFoElffen on 2023-12-27
> **ActionParsnip said:**
> Could just play a YouTube video of the sound in your browser....? Is this not easier or is this a command line only system?
This is exactly what my wife does every night with her phone (with earphones) to help her get to sleep, and encourage the quality of her sleep. She has playlists which she chooses from.

---

### Post by Dennis N on 2023-12-27
> i want to get a sound generator that generates green noise (as opposed to white noise, etc).

FYI,

I looked at Blanket's included sounds. It doesn't generate anything, but uses recorded sound clips and repeats them indefinitely until you stop it. There is no green noise, only white and pink. There is an option to install a custom sound, so if you have a recording, I suppose you could add it.

Screenshot attached.

---

### Post by #&amp;thj^% on 2023-12-27
The OP requested this!
**_" it is important that this works even when the internet is down so this rules out videos on YouTube. any suggestions? "_**

Blanket works for me, and as Dennis N suggested you can add any sound you prefer for Green Noise.

Also Holger_Gehrke links another possible.

---

### Post by ActionParsnip on 2023-12-28
You can grab the audio from YouTube videos and play that as an audio player in Ubuntu etc

---

