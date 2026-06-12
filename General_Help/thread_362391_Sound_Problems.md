---
title: "Sound Problems"
date: 2007-02-15
forum: General Help
---

### Post by Pos on 2007-02-15
I've just installed Ubuntu 6.11 for the first time and I'm trying to set things up and so far things are going ok but I can't get my sound to work I looked in device manager and it lists my soundcard and I've checked alsamixer to see if anything is muted but things seem fine. My Sound card is a Creative Audigy 2 ZS

---

### Post by Gibbs on 2007-02-15
Try this (if you haven't).

Go to **System** > **Preferences** > **Sound**.

Go to the "Sounds" tab and check that "Audigy xx" is set as the default sound card.

---

### Post by Pos on 2007-02-15
I have looked at that and it was set as autodetect but I have also gone through each device listed and tested them but none of them worked, my soundcard audigy wasn't listed either.

---

### Post by puleen on 2007-02-17
I am having the same problem. Sound was working, then I configured dual monitor support with the ATI Radeon card. And all of a sudden sound stopped working. I have an ASUS nVidia Chipset motherboard with onboard sound card.

When I run the tests, nothing happens.

Any suggestions?

---

### Post by Tosa on 2007-02-17
The same problem here. After upgrading to Edgy no sound on Audigy 2 Value. Alsamixer seems to be OK, the card is detected, but no sound...

Help is very welcomed...

---

### Post by Tosa on 2007-02-18
In another thread I've read that someone got the sound back by muting an entry in alsa mixer. So I gave it a try. After muting **Optical Raw** I got my sound back! :guitar:

---

