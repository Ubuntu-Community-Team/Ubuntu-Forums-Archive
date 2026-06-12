---
title: "mpd with pulseaudio in gutsy?"
date: 2007-11-19
forum: General Help
---

### Post by duncan.hawthorne on 2007-11-19
mpd and pulseaudio dont work nicely together
i have pulse audio otherwise working perfectly with the ability to control individual applications volumes etc etc
ive followed the perfect set up for pulseaudio with mpd, but each of them seems to hog the sound card.  [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

if i have any other app working mpd wont play, it says its playing but then finishes playing imediately (ie with no sound)
if i have mpd playing first then i cant use sound in any other programs, and "no sinks" available in pulse audio volume control. other programs with audio grind to a halt and generally crash (without making any sound). ie totem will start showing video then will get slower and slower until it is stopped
if there is no conflict, both work fine at seperate times

however mpd --version shows that it supports pulse output
i even have alsa (and i think oss and esd) all forwarding to pulse, i cant see how there is a problem

i have also compiled the newer release of pulse audio and compiled mpd (in my desperation i even tried svn versions for both) but still the exact same problem. I compile mpd just supporting pulse audio output and it says no output is available

i thought it might be the user mpd was running as ie "mpd", so i tried changing this to root and to myself, but no progress...

any ideas? its the one missing link in my setup....and i dont want to give up on mpd....

---

### Post by Yoshiofthewire on 2007-11-28
I have the same problem, and a workaround.
Here is my workaround:

1) Remove the MPD PulseAudio setting. It still doesn't work, I think the trouble is ether with PulseAudio (they broke it) or with a firewall setting.

2) Setup MPD to use esd

audio_output {
type "ao"
driver "esd"
options "host=127.0.0.1:16001"
name "esd"
}

Note: This is not the configuration from MPD, I changed the host IP address to a real address. I also have a static IP on my system so I use that instead of lo
It works for me this way, and yes I know it is a hack, but PulseAudio is a dropin replacement for esd, so why not use it that way.

:guitar:

---

### Post by duncan.hawthorne on 2008-01-24
i really should have replied to this before. thanks for the help Yoshiofthewire
i used slightly differently:

audio_output {
type    "pulse"
driver "esd"
options "host=localhost"
name "esd"
}

as it said:
couldn't find audio output plugin for type "ao" 
when i used ao (and i couldnt work out what to install)

switching ao to pulse works perfectly for me. hopefully this post will be useful to someone.

---

