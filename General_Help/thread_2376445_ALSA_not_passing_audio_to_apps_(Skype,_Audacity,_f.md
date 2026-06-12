---
title: "ALSA not passing audio to apps (Skype, Audacity, for example)"
date: 2017-11-02
forum: General Help
---

### Post by aa4bb on 2017-11-02
ALSA is not forwarding my audio input to applications, such as Skype and Audacity, although it does send it to Cheese.

With PulseAudio Volume Control (PAVU) open, I select the source (Built-in microphone, etc) and see that it is active under Input. I start the application (Audacity) and start recording. I go to the Recording tab on PAVU and see that the chosen input is active (meter goes up and down with sound). Yet nothing comes through to Audacity. Same results with Skype. However, Cheese does receive the audio when recording.

This problem just started recently, seemingly after a kernel update, but perhaps is a coincidence.

Running Ubuntu 16.04 LTS on Dell E6400 laptop.

---

### Post by aa4bb on 2017-11-03
I finally noticed something on the PAVU Recording tab that I had not previously seen, namely, a Mute button. 

If set to Mute, ALSA doesn't pass the audio to the app, even though the VU on the Recording tab is showing active audio. Once I took off Mute, then Audacity and Skype received the audio and worked as expected. 

The Mute button also seems app specific. That is, I unmuted on Audacity and it worked fine. Then I switched to Skype and there was no audio. Then I noticed the button was muted. Once I unmuted, it worked.

---

