---
title: "Problem with default sound card"
date: 2007-12-08
forum: General Help
---

### Post by h0lix on 2007-12-08
Greetings-

After installing gutsy i couldnt get my sound to work. I have found that both of the cards in my machine work and the onboard for my mobo works fine and for some reason is the default card that is used everytime that i restart my computer. 

```
timo@b0x:~$ cat /proc/asound/modules
 0 snd_via82xx
 1 snd_emu10k1
```

I am trying to get my snd_emu10k1 to be my default (SB audigy)

In using a thread that i found i edited /etc/modprobe.d/alsa-base

adding in:

```
options snd-snd_emu10k1 index=0
options snd-snd_via82xx index=1
```

in hopes of making the audigy my default drive.

Every time that i restart though i can check alsamixer and find that is still uses the via82xx as default.

If switch the audio cables in the back of the machine the sound works fine and i even managed to get my audigy working earlier by disabling a digital switch in the sound control. 

I know the sound card is installed properly and i know that the sound card works, any insight on how to make it default (other than what i have tried) would be greatly appreciated.

thanks.

---

### Post by Baji on 2007-12-16
try:

options snd-emu10k1 index=0
options snd-via82xx index=1

(i think you dont have to double snd)

---

