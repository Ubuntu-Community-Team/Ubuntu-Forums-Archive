---
title: "NVIDIA &amp; ATI Question"
date: 2007-05-17
forum: General Help
---

### Post by nonks on 2007-05-17
(WARNING NOOB QUESTION)

Ok i have a question i wanna know what are NVIDIA & ATI Drivers and i also wanna know where can i find them on my computer

Thanks in advance

---

### Post by hardyn on 2007-05-17
drivers are software that allows the application software to talk to manufacturer specific instructions of the video device.  software is written using a application programming interface, the driver translates these generic commands into commands that the board understands natively. often opengl.


application ---> opengl API -----> driver ------> hardware registers.

depending on what you have, install will have put an appropriate open source driver in automatically... the binary driver packs from ATI and Nvidia are available though synaptic.

---

### Post by nonks on 2007-05-17
thanks alot

---

### Post by borris.morris on 2007-05-17
for ati there are quite a few different ones you can use, mainly radeon, ati, or fglrx. my choice would be radeon. nvidia im not sure about.

---

### Post by hardyn on 2007-05-17
radeon - open source
ati - open source, use radeon unless you have to use ATI
fglrx - closed source.

nv - open source not good for notebooks
nvidia-legacy - closed source
nvidia-glx - closed source
nvidia-glx-new - closed source 
nouveau - open source, in developement

---

### Post by Death_Sargent on 2007-05-17
proprietary or closed source divers tend to take the best advantage of your hardwar but are less compatible with open source 3d apps or rednderers such as AIGLX

---

