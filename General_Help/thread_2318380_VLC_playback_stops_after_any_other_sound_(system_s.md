---
title: "VLC playback stops after any other sound (system sounds etc)"
date: 2016-03-25
forum: General Help
---

### Post by marcus37 on 2016-03-25
Hi,

I am trying to play audio from a network source using VLC on my Raspberry Pi running Ubuntu MATE. It works great until any other sound is played on the system. For example if I change the volume - Ubuntu plays a short sound confirming the new volume - this stops my VLC playback.

I'm not really sure where to look to troubleshoot this. When I run:
```
booyah@RPi:~$ pacmd list-sink-inputs
1 sink input(s) available.
    index: 30
    driver: <protocol-native.c>
    flags: START_CORKED FIX_RATE 
    state: RUNNING
    sink: 0 <alsa_output.0.analog-stereo>
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    muted: no
    current latency: 1015.33 ms
    requested latency: 40.00 ms
    sample spec: float32le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 10
    client: 11 <VLC media player>
    properties:
        media.role = "video"
        media.name = "audio stream"
        application.name = "VLC media player"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "30"
        application.id = "org.VideoLAN.VLC"
        application.version = "2.2.1"
        application.icon_name = "vlc"
        application.language = "en_US.UTF-8"
        application.process.id = "1292"
        application.process.user = "booyah"
        application.process.host = "RPi"
        application.process.binary = "vlc"
        window.x11.display = ":0.0"
        application.process.machine_id = "27d0f826b8d94d039189a976493ee81d"
        application.process.session_id = "c1"
        module-stream-restore.id = "sink-input-by-media-role:video"
```
The output seems to be the same before and after the halt in playback.

Any help would be greatly appreciated!

---

