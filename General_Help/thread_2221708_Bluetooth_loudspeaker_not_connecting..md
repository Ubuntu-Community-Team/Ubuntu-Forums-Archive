---
title: "Bluetooth loudspeaker not connecting."
date: 2014-05-03
forum: General Help
---

### Post by Dan_Keshet on 2014-05-03
I have a new System76 Gazelle computer, with Ubuntu 14.04 installed, and a bluetooth card.

I have two bluetooth devices: a Motorola headset and a Marshall / Stanmore loudspeaker.  I have managed to pair both and see them correctly identified in the bluetooth dropdown.  (This also works using the KDE bluetooth system and blueman.) At first, I could connect to the headset but not play audio through it, but I added the following line to /etc/bluetooth/audio.conf: ```
Disable = Socket
``` I am now able to listen to audio through it.

However, if I click the "Connection" button in the bluetooth menu for the speakers, it remains lit "ON" for only a couple seconds before returning to "OFF".  Similar results happen in both the KDE bluetooth system and blueman application.  I have no trouble connecting to these speakers using my phone and listening to audio through them.

The following line shows up in my syslog and kern.log when I attempt to connect (the number after input increments each time I attempt to connect):

```
May  3 11:15:51 bran kernel: [38223.741968] input: 40:EF:4C:93:55:23 as /devices/virtual/input/input82 
```

---

### Post by Dan_Keshet on 2014-05-03
Some more information here: if I select "Connect to Audio sink..." for the Headset, it fails, while if I select "Connect to headset..." it succeeds.  It seems the problem is connecting to audio sinks in general, not the specific hardware.

---

### Post by Dan_Keshet on 2014-05-03
Working now!  I set Enable = Socket in audio.conf, then ran 
pactl load-module module-alsa-sink device=bluetooth

And that worked!  Still not sure whether it will work on reboot, but at least I'm most of the way there.

---

### Post by airdelroy on 2014-06-21
I am having this same issue exactly.  While I was able to get audio to work with this method, the sound took several seconds to come out the bluetooth speakers.  And it was choppy and often paused half way through the output.  This is not an good solution for me.

Ive read that "Enable=Socket" is not the correct setting for bluez.  However, this is the ONLY way I seem to be able to make my speakers connect.  Any suggestions on how to make the speaker connection with Disable=Socket?

---

### Post by airdelroy on 2014-06-23
I was able to able to finally make this work.  Although I dont understand why its not working.  If I manually enter the command "pactl load-module module-bluetooth-discover" and then connect (with the default bluetooth audio.conf file settings), then the connection works and I can get sound out of the speaker.  There are 2 new sound devices that show up in the sound control for some reason.  The load-module line is present in the pulseaudio default.pa even, so I dont understand why this is working.  But it doesnt tell me that the module is already loaded.  So that load must be failing for some reason.

---

