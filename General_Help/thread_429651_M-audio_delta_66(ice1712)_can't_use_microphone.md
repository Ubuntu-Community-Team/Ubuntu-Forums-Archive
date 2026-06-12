---
title: "M-audio delta 66(ice1712) can't use microphone"
date: 2007-05-01
forum: General Help
---

### Post by hanzomon4 on 2007-05-01
Ok this has been an issue that has hounded me since I started using ubuntu. Basically I can't record anything unless I use jack. Things like skype ekiga(sp) Jokosher don't work. This is the error message I get when testing sound capture in the sound preferences ```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
```  

:confused:

---

### Post by hanzomon4 on 2007-05-02
BuMp!!!!

---

### Post by hanzomon4 on 2007-05-08
Bump again

```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
```

---

### Post by hanzomon4 on 2007-05-09
I got It!! here's how...

The first thing that I did was backup and erase my /etc/asound.conf. I restarted alsa and tested the "Sound Capture" in the gnome-sound-properties, it worked but broke something else. My sound card has 4 output channels and each channel gets split into a stereo pair(8 channels total). I don't have any external way to control my Behringer Truth B2031A monitors(speakers), so I use the softvol plugin in my asound.conf. However I had to delete my asound.conf to get "Sound Capture" to work, so I had a problem. To remedy the situation I had to find out what "devices" were being used to play and record without the asound.conf.  I used speaker-test, aplay and arecord to answer those questions. Long story short they both used default. I also discovered that dmix was enabled by default so I simplified my asound.conf.```
pcm.!default {
    type             plug
    slave.pcm       "softvol"
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "dmix"
    }
    control {
        name        "Master"
        card        0
    }
}

```

This still left me unable to successfully run the "Sound Capture" test. I had to create another pcm device specifically for capture because by defining pcm.!default as dmix left me unable to record, in other words "arecord -f cd -t wav -c 2 -D default  foobar.wav" failed.```
arecord -f cd -t wav -c 2 -D default  foobar.wav
ALSA lib pcm_dmix.c:803:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
arecord: main:550: audio open error: Invalid argument

```

I decided to mirror what I did with pcm.!default and the softvol plugin with a new pcm device. I named the pcm device "pcm.capture" and set the softvol plugin's slave to "dsnoop"(dmix for recording). The new asound.conf passed the speaker test and the arecord test but failed the "Sound Capture" test in gnome-sound-properties. I opened gstreamer-properties and changed the plugin tab to custom and put this in the pipeline box"alsasrc device=capture". I run the test and it worked. To get around setting a custom pipeline I used the "asym" plugin to make "pcm.!default" both a dmixed and dsnooped full duplex pcm device```
pcm.playback {
    type             plug
    slave.pcm       "softvol"
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "dmix"
    }
    control {
        name        "Master"
        card        0
    }
}


pcm.capture {
     type         plug
     slave.pcm   "Rsoftvol"

}

pcm.Rsoftvol {
    type            softvol
    slave {
        pcm         "dsnoop"
    }
    control {
        name        "Rmaster"
        card        0
    }
}


pcm.!default {
  type asym
  playback.pcm "playback"
  capture.pcm "capture"
}


```

---

### Post by tr@ppist on 2007-07-07
Hi hanzomon4,

thanks for sharing your experience, even if what you explain is way too advanced for me (I am an absolute beginner with Linux). I have a M-Audio Delta 44 and I spent the lat 2 days trying to get Skype to work, without success.

I installed envy24control, but it doesn't seem to drive any signal and I am completely lost. In Skype, Options/Sound Devices is set to "Default device" in all the 3 devices (Sound In, Sound Out and Ringing).

Will your suggestions work with a Delta 44 as well? If yes I will give it a try, hoping I do not screw my system up.

Thanks.

---

