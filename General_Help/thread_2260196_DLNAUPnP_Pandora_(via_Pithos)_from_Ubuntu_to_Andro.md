---
title: "DLNA/UPnP Pandora (via Pithos) from Ubuntu to Android"
date: 2015-01-09
forum: General Help
---

### Post by xmbwd on 2015-01-09
So I spent the day trying to make this work -- all to no avail.  I am trying to use my Ubuntu 14.10 to play audio to my AudioEngine speakers using an Android phone as a DLNA/UpNP receiver.  

**SETUP** ---
_Speakers, Powered_:
AudioEngine 5 (*great speakers*)

_Android Phone_:  
Installed AirPin (or AirReceiver) -- both allow the phone to act as a DLNA/UpNP device
Turned on
[**NOTE:** I tested this setup with another Android phone running AllStream, and the AirPin phone received the music from the AllStream phone -- with a 3 second delay).
[U]
Ubuntu 14.10[/U]:
[I]**Pithos**
[/I]Installed.  

***Rygel/PulseAudio***
Followed instructions [here]("https://wiki.gnome.org/Projects/Rygel/Pulseaudio") to use Rygel/PulseAudio to stream audio to DLNA/UpNP devices (unfortunately, this guide cuts out at "Enable the External plugin for Rygel and exporting of the [PulseAudio]("https://wiki.gnome.org/PulseAudio") media server by creating a file....." and then resumes with "with the following content."  So I don't know where to create that file!!!).

After installing that, I went to PulseAudio Preferences and changed the settins to the below:

[IMG]https://dl.dropboxusercontent.com/u/13392425/PulseAudio%20Network%20Access.png[/IMG]

[IMG]https://dl.dropboxusercontent.com/u/13392425/Pulse%20Audio%20Network%20Server.png[/IMG]

Then, in Pulse Audio Volume Control (as well as the volume control in Sound), I could see DLNA/UPnP streaming and my Android phone (LG-MarqueeAir) -- I could also see my Denon receiver:

[IMG]https://dl.dropboxusercontent.com/u/13392425/Volume%20Control.png[/IMG]

I can select the "DLNA/UPnP Streaming" under "Playback" and Pulse Audio Volume Control shows the volume bounce up and down.  But I'm not sure how to access the "DLNA/UPnP Streaming" stream from the device.

On the other hand, when I select "AirReceiver" (the Android Phone), it seems to be fine, but the volume indicator does not bounce.  Indeed, this actually stops the streaming from Pithos.  That is, when I have Pithos playing and I select either of the DLNA/UPnP devices, the music does **not** play, and -- it actually "pauses" from streaming/playing.  I can select "Speakers - Built-in Audio" and the music will restart.

I feel like I am *really, painfully* close.  Just one switch or something away.

Has anyone got this working???  So. . . close.....

---

### Post by xmbwd on 2015-01-23
Geez, no one???  I would have thought folks would jump on this.  Everyone has old Androids laying around.  And -- if this worked -- it would be a free alternative to the very expensive Sonos.

---

### Post by xmbwd on 2015-01-25
I don't know if this helps figure out the problem -- but whenever I have the audio Playback on Pulse Audio Control set to the DLNA receiver (as opposed to internal speakers) it _**pauses playback **_on the program.  That is the case with Pithos, Rythmbox, or FireFox using YouTube.   

And it won't let me restart the playback until I switch back to the built-in speakers.

---

