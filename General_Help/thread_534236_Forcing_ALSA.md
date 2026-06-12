---
title: "Forcing ALSA"
date: 2007-08-25
forum: General Help
---

### Post by malfist on 2007-08-25
I have a problem, when I run TeamSpeak, it uses (and only uses) OSS. I don't have a multichannel soundcard. So when I run the game I'm using TeamSpeak for, I can hear anything. How can I force teamspeak to use ALSA like through AOSS? It has an option to use a device and default is /dev/dsp using .asoundrc I have this:
```

pcm.ossmix {
    type dmix
    ipc_key 1021          # must be unique!
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024  # must be power of 2
        buffer_size 8192  # dito. It
        #format "S32_LE"
        #periods 128      # dito.
        rate 48000
    }

# bindings are cool. This says, that only the first
# two channels are to be used by dmix, which is enough for
# (most) oss apps and also lets multichannel chios work 
# much faster:

    bindings {
        0 0   # from 0 => to 0
        1 1   # from 1 => to 1
    }
}

# Redirect to ossmix
pcm.!default {
    type plug
    slave.pcm "ossmix"     # use our new PCM here
}

# Redirect to ossmix
pcm.dsp0 {
    type plug
    slave.pcm "ossmix"     # use our new PCM here
}

# mixer0 like above
ctl.mixer0 {
    type hw
    card 0
}
```
which is supposed to make a device that acts as OSS but uses ALSA, how can I use this for teamspeak?

---

