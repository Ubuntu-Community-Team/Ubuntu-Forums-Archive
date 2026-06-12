---
title: "really crappy fullscreen video"
date: 2005-10-22
forum: General Help
---

### Post by renzokuken on 2005-10-22
hi, 

i finally finshed installing ubuntu. i had to do a 'server' install for reasons discussed in another thread. once that was done i did a 

```
sudo apt-get install xubuntu-desktop gdm
```

to get XFCE as my desktop

anyways, i used synaptic to install all the codecs and libx11 and libxv and then mplayer-386. all videos work fine in 'original size' but as soon as i fullscreen the video, the refresh rate drops heavily, the sound and video go heavily out of sync and i get this weird 'shear line' appear on the screen every so often......

does anyone know what might cause this problem, ive tried xine-ui and vlc as well and they both give the same problem

i dont fancy watching all my videos in small screen >_<    

thanks

---

### Post by docomo on 2005-10-22
This sounds like the symptoms I once got when xorg was configured wrongly so that xv wasn't working. To fix it I had to edit xorg.conf. Unfortunately I don't remember exactly what I had to change, but somebody else can probably give you more information.

---

### Post by renzokuken on 2005-10-22
thanks for that anyway dude......its a starting point so i'll do some googling

dont suppose theres any change u could post your xorg.conf file is there?

but if anyone has any ideas please help me........

---

### Post by docomo on 2005-10-22
Under Section "Device" in xorg.conf I have this:

> # === Video Overlay for the Xv extension ===
        Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
        Option "OpenGLOverlay" "off" 
That seems relevant. Do you have that? I have a radeon card and use the fglrx driver by the way.

---

### Post by renzokuken on 2005-10-23
that sounds very relevant yes.....i also have a radeon card (9800) but my xorg.conf file says "generic video card" etc.

so if i install the fglrx driver (which i have no idea how to do by the way so any help there would be awesome) and then edit my xorg.conf to add the bit u wrote in the post above it should be ok

cheers

---

### Post by renzokuken on 2005-10-23
ok.......i installed the fglrx drivers according to a post i found elsewhere on the forums

guess what, problem solved......wahey.......didnt even have to change my xorg.conf file (manually anyway)

so thanks for your help docomo

---

