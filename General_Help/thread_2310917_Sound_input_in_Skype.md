---
title: "Sound input in Skype"
date: 2016-01-23
forum: General Help
---

### Post by afrancis-ozonline on 2016-01-23
When I go to preferences in skype it shows sound in as Pulse Audio. How do I change this to my Webcam microphone?
I am using Ubuntu 15.10.

---

### Post by Vladlenin5000 on 2016-01-23
You can either select it in the OS sound settings or, at Skype, click Open PulseAudio settings and change it there.

---

### Post by afrancis-ozonline on 2016-01-23
Webcam is selected in Sound in Settings. I cannot open Pulse Audio in Skype. Now what?

---

### Post by Vladlenin5000 on 2016-01-23
Why can't you? It's a button which says precisely that... So, what happens?

---

### Post by afrancis-ozonline on 2016-01-23
When I click on Microphone >" PulseAudio Server (local)" in Skype Sound Devices it just becomes highlighted and nothing else happens.
The message underneath the options reads " It appears your system has PulseAudio running to change sound settings you need to use your Desktop Manager volume control or PulseAudio volume control"

---

### Post by Bucky Ball on 2016-01-24
Make a test call, open PulseAudio Volume Control (install from SCentre if you haven't already), set the Input, Output and playback devices.

If you go to the playback tab while making a test call you should see the Skype audio stream there. Change the device it is using to the webcam from the dropdown box.

Skype uses Pulseaudio to access the machine's audio, you use PAVControl to tweak the sound settings, not Skype. ;)

---

### Post by afrancis-ozonline on 2016-01-24
Thanks very much. Test call in Skype now seems to work.
Very grateful for your help.

---

