---
title: "does anyone know how to get Mycroft's Mimic 2 TTS installed on Lubuntu"
date: 2020-02-09
forum: General Help
---

### Post by ardouronerous on 2020-02-09
Running Lubuntu 18.04.

Mycroft's Mimic 2 voice is the most natural sounding I've heard, specifically the April 2018 voice, here's the samples: [https://mycroft.ai/blog/available-voices/](https://mycroft.ai/blog/available-voices/)

My question is, is Mycroft's Mimic 2 TTS free? If it's free, is there a way to install it on my system? My purposes for the TTS is to read the clipboard with a press of a button, so I can listen to Wikipedia articles and such.

Is there a way to do this without PPAs? Like snap or flatpaks? Thanks.

---

### Post by Holger_Gehrke on 2020-02-10
Doesn't seem that way. As a matter of fact, it seems that installing from source is the only way to get it to run. And even that won't get you the quality you want. Mimic 2 is based on Keith Ito's open source implementation of google's tacotron idea. It's basically a neural net implemented using tensorflow to generate speech. This net has to be trained on text and recordings of the spoken text. While the source of mimic is freely available, the input they used to train it isn't, AFAIK. They actually state that if you install Mycroft and Mimic 2 locally and don't use their service for the Mycroft assistant to generate speech you should expect lower quality / a 'robotic' sounding voice


Holger

---

### Post by ardouronerous on 2020-02-10
Thanks for the reply  Holger.
I guess I'm stuck using Wine and my SAPI5 voices. The reason why I wanted to install Mycroft's Mimic 2 TTS is because I didn't want to rely on Wine for my TTS needs, I wanted to use a TTS that is native to Linux, but didn't sound as robotic.

Thanks again.

---

