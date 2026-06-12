---
title: "Deactivate integrated device"
date: 2008-06-18
forum: General Help
---

### Post by das letzte einhorn on 2008-06-18
This is a follow up from this thread : [http://ubuntuforums.org/showthread.php?t=830539](http://ubuntuforums.org/showthread.php?t=830539) . However, because the problem seems to be totally different now, I felt that it was appropriate to create a new thread about it.

After talking on the PulseAudio IRC channel, it seems that my problem is related to ALSA configuration. I believe that the audio streams are being sent to my integrated audio device instead of my sound card; I would want the latter instead. I was wondering if there is a way in Ubuntu to deactivate a particular hardware piece such as integrated audio, and afterwards which files/configuration scripts I need to run for the streams to be send to my actual sound card and therefore that I test appropriately the recommended configuration described here : [http://ubuntuforums.org/showthread.php?p=4451132](http://ubuntuforums.org/showthread.php?p=4451132) . 

Thanks!

---

### Post by iaculallad on 2008-06-18
You can change your Sound Card priority. Open your terminal and issue the commands below.

List detected Sound cards:

```
asoundconf list
```

This should output the detected sound card(s). Take note of the name for your external sound card.

We set the external sound card as default for Ubuntu:

```
sudo asoundconf set-default-card external_sound_card_name
```

external_sound_card_name = the name listed using the **asoundconf list** command.

---

### Post by das letzte einhorn on 2008-06-18
Proceeding with your commands has helped me so far to recover audio when PulseAudio is killed with some Ubuntu applications (VLC media player, youtube, Gnome Mplayer, WINE), but others do not work (TuxGuitar / Timidity, Exaile media player, no sound at startup). I will see if this will survive after a few reboots.

When running PA however, there is no audio whatsoever which comes out from any applications. Yet, the streams are still being detected by pulseaudio, and the volume meter detects variations in the audio streams. The burning problem right now is to find if the issue comes from PA or from ALSA. Is there anybody here which is somewhat knowledgeable with PA and ALSA and which could provide me with tests to do, and which other data I should provide?

---

### Post by iaculallad on 2008-06-18
Navigate to System->Preferences->Sound, under the "Devices" tab, try to change "AutoDetect" values to "ALSA - Advanced Linux Sound Architecture" of your "Sound Events" and "Music and Movies".

---

### Post by das letzte einhorn on 2008-06-18
All of them right now are set to PulseAudio. Are you sure I should change any of this? My previous experience when I did that was that I lost all the audio again. Is there anything else I should do afterwards?

---

### Post by iaculallad on 2008-06-18
You could give it a try and revert the values back to its original values if it does not work.

---

### Post by das letzte einhorn on 2008-06-19
Despite reverting them, I have indeed lost the audio stream. Could it be that the default configuration gets lost at the same time?

EDIT: The reason why is that Pulseaudio got reactivated. After killing the process, sound came back again. On the other hand, this is really annoying. Could it be a better idea to just uninstall PulseAudio and only keep ALSA? So far it looks more like an annoyance than something useful.

---

### Post by das letzte einhorn on 2008-06-19
Bump

---

