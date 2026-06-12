---
title: "PulseAudio not working"
date: 2007-11-05
forum: General Help
---

### Post by ~LoKe on 2007-11-05
I'm absolutely confused with how to get pulse audio working.  I installed it like so:

> sudo apitude install pulseaudio libao-pulse libgstreamer-plugins-pulse0.10-0 libpulse0 libpulse-browse0 libpulse-mainloop-glib0 padevchooser paman paprefs pavucontrol pavumeter pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-lirc pulseaudio-module-X11 pulseaudio-module-zeroconf pulseaudio-utils
Then ran: > asoundconf set-pulseaudio
And rebooted.

Now, I've got absolutely no sound.  I tried opening the pulse audio controls (volume manager, etc) and I get connection errors...connection to what?

Now I'm lost, and have no sound.  What did I do? o_O

---

### Post by qamelian on 2007-11-05
You may want to start by looking here:
[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by ~LoKe on 2007-11-05
> **qamelian said:**
> You may want to start by looking here:
[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

My brain shuts down when I look at that page.  I did a brief scan and didn't see anything particular about connections.  I followed the first few steps which would be the basic setup of PA.  After that I skipped all the application configurations and simply trying.

> mplayer -ao *.avi
And no sound devices were detected.

---

### Post by qamelian on 2007-11-05
Not sure what else to tell you. That page helped me get PulseAudio working on my desktop. No joy on my laptop though.

---

### Post by ~LoKe on 2007-11-05
After various "hacks", I've gotten it to work!  Only major problem now is that it's playing the sound through my headphones (/dev/dsp1) rather than my speakers (/dev/dsp).  How would I go about fixing this?

---

### Post by ~LoKe on 2007-11-05
Heh, wow, this is going well.  Figured out my device problem.  It's great being able to play music and watch a video online and have sound from both devices.  Finally sound in Linux is up to par with Windows.

Now...I only have one problem that I'm aware of (two, really, but one isn't a big deal).

1.  MPD won't play.  I click "play", it loads the song, then stops.  Doesn't play a sound.
I added this into /etc/mpd.conf:
> audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
	server  "localhost"   # optional
        sink    "alsa_output" # optional
}
Is that not correct?  Here are the important lines in ~/.asoundrc
> pcm.dsp2 {                                                                                               
type plug                                                                                                
slave.pcm "pulse"                                                                                        
}                                                                                                        
                                                                                                            
pcm.pulse {                                                                                              
type pulse                                                                                               
}                                                                                                        
                                                                                                            
ctl.pulse {                                                                                              
type pulse                                                                                               
}                                                                                                        
                                                                                                            
pcm.!default {
type pulse
slave {
rate 48000
pcm "spdif"
}
}                                                                                                    
                                                                                                            
ctl.!default {                                                                                           
type pulse                                                                                               
}  

Am I doing something wrong?

Problem #2: I'm trying to play Enemy Territory while listening to music, but to this day I haven't been able to.  I can only have sound from one at a time.  Now that I have pulseaudio, I guess my question is...can I modify ET to make use of it, and have both play at once?

---

### Post by groggyboy on 2007-11-10
i tried to get mpd running with PulseAudio as well.  unfortunately, i had the same problems as you.  eventually, i gave up and switched to a non-mpd player.  which made me sad.  i've updated my version of PA to the new one since then, so i might try again.  i also wanna try compiling the svn version of mpd to see if that works.

let me know if you've had success.

---

### Post by Yoshiofthewire on 2007-11-22
I have the same problem, and a workaround.
Here is my workaround:

1) Remove the MPD PulseAudio setting.  It still doesn't work, I think the trouble is ether with PulseAudio (they broke it) or with a firewall setting.

2) Setup MPD to use esd

audio_output {
        type      "ao"
        driver    "esd"
        options   "host=127.0.0.1:16001" 
        name      "esd"
}

Note: This is not the configuration from MPD, I changed the host IP address to a real address.  I also have a static IP on my system so I use that instead of lo
It works for me this way, and yes I know it is a hack, but PulseAudio is a dropin replacement for esd, so why not use it that way.

:guitar:

---

### Post by OliW on 2008-01-22
I'm in the same situation that you started in. The pulseaudio-manager says it can't connect. No sound. Can't revert back to ALSA. Complete nightmare.

I don't suppose you can remember how you got it all fixed because I'm going potty without my music =(

---

