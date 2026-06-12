---
title: "Ubuntu 20.04 LTS bad audio"
date: 2020-06-30
forum: General Help
---

### Post by thusspokelong on 2020-06-30
I have a [msi gt780dxr]("https://www.msi.com/Laptop/GT780DXGT780DXR/Specification")  that a friend gave me. I just clean installed Ubuntu 20.04 LTS, previously  had 18.04 LTS installed. It runs great, responsive, everything I like  about Ubuntu. I use this laptop for streaming, watching movies, and retro gaming through my home theater TV/receiver connected through HDMI. I have turned the sound on the laptop off.   

However, there is one problem: 


The  audio is terrible. To the best of my knowledge I have installed NVIDIA proprietary drivers for the  video card. Cannot seem to see any options at all for audio drivers. It sounds tinny, delayed/clipping on the start from a pause, just poor sound quality overall. Ubuntu 18.04 LTS audio was fine.


Any suggestions?

PS - I always seem to have trouble with video/audio drivers when using Ubuntu. I want to fully switch all my personal PCs over to Linux (to hell with Windows) but this is the one thing that always hangs things up for me. I wish I could take a lesson. I can install Ubuntu fine with no problems. The next step of tweaking the display and sound (and hardware drivers) is always a bugbear for me. And I am never quite sure what I am missing or even after a change if I've actually done the right move or if there is some better option that I am just ignorant of. My usual method of attempting to solve this perpetual problem is to randomly try one suggestion after another from google searching, I wish I could *actually know* what to do.

---

### Post by haytham-med on 2020-06-30
Try pulse audio volume control, pavucontrol, then switch built-in audio in configuration, Hope that helps.

---

### Post by thusspokelong on 2020-06-30
> **haytham-med said:**
> Try pulse audio volume control, pavucontrol, then switch built-in audio in configuration, Hope that helps.
Thanks. It might in fact help I'm just not sure how to do all that. :) 

Would this work the same in 20.04 [https://linuxhint.com/pulse_audio_sounds_ubuntu/](https://linuxhint.com/pulse_audio_sounds_ubuntu/)

---

### Post by thusspokelong on 2020-06-30
That worked! Thanks haytham-med.

---

