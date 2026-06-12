---
title: "can't play .movs"
date: 2005-09-21
forum: General Help
---

### Post by nevle on 2005-09-21
hi, i've installed all the packages mentioned in the starter pack for playing .movs but get an error in mplayer saying "FATAL Could not initialize video filters(-vf) or video output(-vo)" what am i doing wrong?As far as i know i,ve got all the codecs installed(inc w32).help ](*,)

---

### Post by TristanMike on 2005-09-21
Hi, which video player are you using? I recommend a little beauty called VLC (Video Lan Client). It is perhaps arguably the best video player out there. Plus I believe it comes with it's own codecs. You can get VLC via Synaptic or by ```
sudo apt-get install vlc
```Try that and see what you get.

---

### Post by peterthewolf on 2005-09-21
I got both VLC and Totem to display films by running easybuntu or automatix see forums. On of these puts libdvdcss2 into synaptic which is needed to decrypt.

---

### Post by nevle on 2005-09-21
thanks guys,installed vlc and it works -but totem or mplayer still don't?? totem shows pic then freezes, mplayer just plays sound (when playing .mov) if i run easyubuntu now willit kill vlc?

---

### Post by TristanMike on 2005-09-21
Ok, you might want to try installing the libdvdcss2 package as peterthewolf suggested. Also try installing totem-xine, you can do both by ```
sudo apt-get install libdvdcss2 totem-xine
```or from "Synaptic" if that feels safer, either way give that a go too.

I can view .mov's but I have experienced a .mov to play the video but no sound, and vlc to play the sound but no video, it was only a short clip so I didn't care or look into why that particular file did it because I just sync'd the two programs together, it was annoying, but like I said, it was 1 very short obscure .mov file and it's only been the once.

---

