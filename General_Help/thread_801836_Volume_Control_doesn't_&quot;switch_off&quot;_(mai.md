---
title: "Volume Control doesn't &quot;switch off&quot; (main) Speaker"
date: 2008-05-20
forum: General Help
---

### Post by Solrac924 on 2008-05-20
i notice the other day that plugging in my headphones doesn't cut off the volume to my main speakers. i read that i must manually do so in the Volume Control. 
    in the Volume Control there are 2 tabs: Playback & Switches. in the Switches tab, i see Headphones & Speaker. when i uncheck Speaker, there is no change (i can still hear sound from my headphone & the computer speakers). 
    what can i do? i've read i can make changes to the audio driver by entering the following in the terminal: sudo gedit /etc/modprobe.d/alsa-base. please help. :???:

---

### Post by sdennie on 2008-05-20
You could try clicking Edit->Preferences in the volume control app and see if you can add a volume control for the headphones.

---

### Post by Solrac924 on 2008-05-21
thanks, but i think i was misunderstood. i'm trying to turn off the main speakers, or at least lower the speakers only. 

the preferences adds sliders to a Center, Surround, Side, Microphones, & Input Sources will i don't have. 

Anyone with knowledge of a fix please help.

---

### Post by drs305 on 2008-05-21
On my lenovo laptop, double clicking the volume control brings up the control panel. On my machine, the switch to kill the external speakers is labeled 'External Amplifier'. From what I gather, you don't have that tick box under any of your tabs?  You might try running 'alsamixer' and seeing if it appears or if you can gain control through that panel.

---

### Post by Solrac924 on 2008-05-22
Alsamixer shows headphone volume is at 00, yet i'm getting sound. everything else the volume affects, the headphone does too. :?

---

### Post by drs305 on 2008-05-24
Solrac924,

I haven't seen a resolution to your problem so I fired up my laptop to see if I could provide any more clues. You stated you didn't have the "External Amplifier" tick box. Just for reference, in System > Preferences > ****Sound, Devices, I have the Sound Events/Music and Movies and Audio Conferencing all set to ALSA - Advanced Linux Sound Architecture, and the Default Mixer Tracks are set to HDA Intel (ALSA mixer).  

When I double click the speaker volume on the panel, the control panel title is "Volume Control: HDA Intel (ALSA Mixer).

I don't know if those settings are on your laptop but thought I'd give you something else to try if you still can't kill your external speakers.

Good luck.

---

### Post by Solrac924 on 2008-05-29
thanks drs305, but no, that didn't work. that's too bad...i was having a good feeling on that one.
i did what you told me to do: put Sound Events, Music and Movies, Audio Conferencing (Sound Playback) all on ALSA. i also have my Default Mixer Tracks on HDA ATI SB. :?

anything else i can try? anyone please?  :(

---

