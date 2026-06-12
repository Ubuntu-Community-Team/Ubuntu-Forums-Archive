---
title: "sound in vmware / flash while running jackd?"
date: 2007-07-21
forum: General Help
---

### Post by rawdigit on 2007-07-21
The situation is the following with my current configuration:
with jack not running:
- multiple alsa clients can play sound simultaneously via dmix
- multiple flash videos in firefox can play sound additional to those

with jack running:
- multiple alsa clients can play simultaneously via alsa-jack plugin
- flash videos play no sound

VMware always can only play sound when there is no other software using the soundcard (checked by lsof | grep snd // lsof | grep pcm).

My questions:
1) Is it possible to change the .asoundrc file so that the alsa-oss emulation uses the alsa-jack plugin instead of dmix?
2) How can I make VMWare to play sound via jackd? I need to use it to run windows music production software that I can't run with wine.
3) How can I make flash videos play sound while running jackd? 

Here is my .asoundrc:
```

######################## DMIX ########################

pcm.snd_card {
  type hw
  card 0
}

ctl.snd_card {
  type hw
  card 0
}

pcm.dmixer {
        type dmix
        ipc_key 1024
	ipc_perm 0666
	slave.pcm "snd_card"
        slave {
		pcm "hw:0"
                period_time 0
                period_size 1024
                buffer_size 4096
                format S32_LE
        }
	bindings {
		0 0
		1 1
	}
}

pcm.dsnooper {
  	type dsnoop 
	ipc_key 2048
	ipc_perm 0666
	buffer_size 4096
	slave {
                period_time 0
                period_size 1024
                buffer_size 4096
                format S32_LE
	}
}

pcm.duplex {
	type asym
	playback.pcm "dmixer"
	capture.pcm "dsnooper"
}

######################## OSS ########################
pcm.dsp "duplex"
pcm.dsp1 "duplex"

ctl.dsp {
    type plug
    slave.pcm "snd_card"
}

ctl.mixer {
    type plug
    slave.pcm "snd_card"
}


######################## JACK ########################
pcm.jackplug {
        type plug
        slave { pcm "jack" }
}

pcm.jack {
        type jack
        playback_ports {
                0 alsa_pcm:playback_1
                1 alsa_pcm:playback_2
        }
        capture_ports {
                0 alsa_pcm:capture_1
                1 alsa_pcm:capture_2
        }
}


###################### DEFAULT ######################
pcm.!default {
	type plug
	slave.pcm "jackplug"
	#slave.pcm "duplex"
}
```

---

### Post by rawdigit on 2007-07-22
anyone?

---

