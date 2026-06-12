---
title: "Damaged .WAV file"
date: 2019-11-14
forum: General Help
---

### Post by spjackson on 2019-11-14
I have a portable Digital Voice Recorder which records audio and saves in .WAV format. This normally works fine but on the odd occasion the .WAV file is damaged in some way. At present I have such a recording. I usually edit the recording in Audacity, but when Audacity opens it, the track is empty (length 0s). Windows Media Player won't play this particular file, nor will Microsoft's Edge. Lame won't process it. sox produces an output file of 60 bytes. However, VLC Media Player will successfully play all 80 minutes of the recording. This is the only program I have found so far that is able to do anything reasonable with this broken file but VLC doesn't have a method to save in a different format, does it?

Is there a tool that will read this particular broken .WAV and convert it to something good that Audacity can load?

The low-tech method I have thought of is to play it in VLC Media Player and re-record what is being played, but apart from being time-consuming, that strikes me as a bit of a dumb approach.

---

### Post by Holger_Gehrke on 2019-11-14
vlc can convert and save all files it can open and play."Menu"->"Media"->"Convert/Save" should be what you're looking for.

Holger

---

### Post by spjackson on 2019-11-14
> **Holger_Gehrke said:**
> vlc can convert and save all files it can open and play."Menu"->"Media"->"Convert/Save" should be what you're looking for.

Thank you so much. Why didn't I notice that? That's worked.

---

