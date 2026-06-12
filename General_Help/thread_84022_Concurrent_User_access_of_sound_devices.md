---
title: "Concurrent User access of sound devices"
date: 2005-10-30
forum: General Help
---

### Post by ToonArmy on 2005-10-30
Hey, I am having problems with sound (as the title hints). Basically no two users can access ALSA at the same time, you get permission denied erros turfed up. Why does this bother me you ask?

Well I use [mpd]("http://www.musicpd.org/") to play music, this runs as another user (mpd). So gaim notification are not played, this is really starting to annoy me.

I have ran totem/mplayer/aplay as other users and exibit the same problem, this used to run perfectly fine on Hoary.

The problem is also exhibited using the switch user feature in gdm, if one user leaves totem playing away no other user can access the sound device.

Any help is appreciated.

aplay error:
```
ALSA lib pcm_dmix.c:773:(snd_pcm_dmix_open) unable to create IPC semaphore
aplay: main:533: audio open error: Permission denied
```

---

### Post by ToonArmy on 2005-11-02
Anyone? *sigh*

---

### Post by aminalshmu on 2005-11-19
[http://ubuntuforums.org/showthread.php?t=72163&highlight=mpd](http://ubuntuforums.org/showthread.php?t=72163&highlight=mpd)

---

### Post by Slalomsk8er on 2006-01-31
The link is nice and fixed it (just a workaround) but the multiuser concept is still broken and I don't like to run servers under my user (I know I am paranoid) :(

This is my config:

```
#cat  /etc/asound.conf
pcm.nforce-hw {
        type hw
        card 0
}

pcm.!default {
        type plug
        slave.pcm "nforce"
}

#0,0 is analog out (i.e. headphone socket on the shuttle), 0,1 and 0,2 is 
#spdif out (0,1 is optical and 0,2 is electrical spdif).

pcm.nforce {
        type dmix
        ipc_key 1234
        slave {
                pcm "hw:0,2"
                period_time 0
                period_size 1024
                buffer_size 32768
                rate 48000
        }
}

ctl.nforce-hw {
        type hw
        card 0
}
```

```
#cat /etc/mpd.conf 

port "6600"
music_directory "/home/myUser/data/sound"
playlist_directory "/var/lib/mpd/playlists"
log_log_file "/home/myUser/mpd.log"
#log_file ""/var/log/mpd.log
error_file "/home/myUser/mpd.error.log"
#error_file "/var/log/mpd.error.log"

filesystem_charset "UTF-8"

state_file "/var/lib/mpd/state"

mixer_type              "alsa"
mixer_device            "default"
mixer_control           "PCM"

# ALSA Audio Output
ao_driver               "alsa09"
ao_driver_options       "dev=default"

user "myUser"
```
all commented && unimportant  lines cut out and no, myUser is not my login ;)

---

