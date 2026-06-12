---
title: "No audio whenever Kernel gets updated (Dummy Output)"
date: 2023-04-04
forum: General Help
---

### Post by n8mills on 2023-04-04
Hi all,

I've gotten to the point I'm reinstalling Ubuntu from scratch every time a new kernel comes out because it always breaks my HDMI audio.  This time not even that worked.  Tempted to move on to other distros becuase I've tried easily a dozen troubleshooting steps based on searching around and this seems like a perennial issue.  Anyway, here are steps I tried today based on a recent thread here:

```
lspci -vnn
```

Audio-specific Output:
```
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: ASUSTeK Computer Inc. FCH Azalia Controller [1043:8445]
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```
Then:
```
pacmd list-sink-inputs
```

output:
```
1 sink input(s) available.
    index: 10
    driver: <protocol-native.c>
    flags: START_CORKED FIX_RATE 
    state: RUNNING
    sink: 0 <auto_null>
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    muted: no
    current latency: 1139.85 ms
    requested latency: 40.00 ms
    sample spec: float32le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 10
    client: 20 <VLC media player (LibVLC 3.0.18)>
    properties:
        media.role = "video"
        media.name = "audio stream"
        application.name = "VLC media player (LibVLC 3.0.18)"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.VideoLAN.VLC"
        application.version = "3.0.18"
        application.icon_name = "vlc"
        application.language = "en_US.UTF-8"
        application.process.id = "6883"
        application.process.user = "n8"
        application.process.host = "n8-CM1735"
        application.process.binary = "vlc"
        window.x11.display = ":0"
        application.process.machine_id = "7082466a0a4b45b88bf57295f6e2d1e8"
        module-stream-restore.id = "sink-input-by-media-role:video"

```



Then:
```
alsamixer -V all
```

```
&#9474; Card: HD-Audio Generic                               F1:  Help               &#9474;
&#9474; Chip: Realtek ALC887-VD                              F2:  System information &#9474;
&#9474; View: F3: Playback  F4: Capture  F5:[All]            F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -21.00]                       Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;    &#9484;&#9472;&#9472;&#9488;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;     &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;     &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;     &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;     &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;     &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;     &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#8594;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;      &#9474;     &#9474;      &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;   &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                   &#9474;OO&#9474;     &#9474;MM&#9474;                       &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                  &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                       &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;                                                                              &#9474;
&#9474;      39    100<>100 100<>100 100<>100   0<>0     0<>0     0<>0   100<>100    &#9474;
&#9474;  < Master >Headphon   PCM     Front   Front Mi Front Mi Front Mi Surround 
```


That all seems ok.

Not sure what else to try, can somebody help further?

---

### Post by #&amp;thj^% on 2023-04-04
They kind of dumped us with a Pulseaudio/Pipewire session, and it doesn't mix well with system core changes.
I dumped Pulseaudio over a year ago and couldn't be happier:
```
pacmd list-sink-inputs
No PulseAudio daemon running, or not running as session daemon.

```
Now:
```
systemctl status --user pipewire wireplumber
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: e>
     Active: active (running) since Tue 2023-04-04 08:39:16 MDT; 4h 8min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 7402 (pipewire)
      Tasks: 2 (limit: 9074)
     Memory: 9.2M
        CPU: 376ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;7402 /usr/bin/pipewire

Apr 04 08:39:16 me-Lenovo-Legion-5-15ARH05 systemd[7019]: Started pipewire.serv>
Apr 04 08:39:16 me-Lenovo-Legion-5-15ARH05 pipewire[7402]: mod.rt: Can't find o>
Apr 04 08:39:16 me-Lenovo-Legion-5-15ARH05 pipewire[7402]: mod.rt: found sessio>

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset>
     Active: active (running) since Tue 2023-04-04 08:39:16 MDT; 4h 8min ago
   Main PID: 7406 (wireplumber)
      Tasks: 5 (limit: 9074)
     Memory: 14.9M
        CPU: 4.277s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
lines 1-23


```
If your willing or up for another adventure see this: [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e)
And follow every command shown on that page.
Good Luck

---

### Post by n8mills on 2023-04-04
Well that changed a bunch of things it seems like, but still no audio

```
me@me-comp:~$ systemctl status --user pipewire wireplumber
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-04-04 15:39:06 PDT; 17min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1653 (pipewire)
      Tasks: 2 (limit: 6372)
     Memory: 7.5M
        CPU: 7.047s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1653 /usr/bin/pipewire


Apr 04 15:39:06 me@me-comp systemd[1617]: Started PipeWire Multimedia Service.


&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-04-04 15:39:06 PDT; 17min ago
   Main PID: 1660 (wireplumber)
      Tasks: 4 (limit: 6372)
     Memory: 6.1M
        CPU: 611ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;1660 /usr/bin/wireplumber


Apr 04 15:39:06 me-comp systemd[1617]: Started Multimedia Service Session Manager.
Apr 04 15:39:07 me-comp wireplumber[1660]: **Failed to set scheduler settings: Operation not permitted
```**

---

### Post by n8mills on 2023-04-04
Worth noting that this was the desired outcome in that gist.github but it hasn't alleviated my issue:

```
me@me-comp:~$ LANG=C pactl info | grep '^Server Name'
Server Name: PulseAudio (on PipeWire 0.3.48)
```

---

### Post by #&amp;thj^% on 2023-04-04
Lets have a look at:
```
aplay -l
```

---

### Post by n8mills on 2023-04-04
Thanks for your engagement

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by n8mills on 2023-04-04
alsamixer:

&#9474; Card: PipeWire                                                                                        F1:  Help               &#9474;
&#9474; Chip: PipeWire                                                                                        F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                              F6:  Select sound card  &#9474;
&#9474; Item: Master                                                                                          Esc: Exit               &#9474;
&#9474;                                                                                                                               &#9474;
&#9474;                                                                                                                               &#9474;
&#9474;                                                                                                                               &#9474;
&#9474;                                                             &#9484;&#9472;&#9472;&#9488;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9474;&#9618;&#9618;&#9474;                                                              &#9474;
&#9474;                                                             &#9500;&#9472;&#9472;&#9508;                                                              &#9474;
&#9474;                                                             &#9474;OO&#9474;                                                              &#9474;
&#9474;                                                             &#9492;&#9472;&#9472;&#9496;                                                              &#9474;
&#9474;                                                           100<>100                                                            &#9474;
&#9474;                                                          < Master >

---

### Post by n8mills on 2023-04-04
OK so I changed the soundcard on alsamixer, now I see this:

&#9474; Card: HD-Audio Generic                                                                                F1:  Help               &#9474;
&#9474; Chip: Realtek ALC887-VD                                                                               F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                              F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -18.00]                                                                        Esc: Exit               &#9474;
&#9474;                                                                                                                               &#9474;
&#9474;                                                                                                                               &#9474;
&#9474;                                                                                                                               &#9474;
&#9474;   &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                              &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#9474;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#8594;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#9474;
&#9474;   &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;                              &#9474;
&#9474;   &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;   Enabled    2ch    Disabled &#9474;
&#9474;   &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;OO&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;                                       &#9474;
&#9474;   &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                                       &#9474;
&#9474;    45    100<>100 100<>100 100<>100   0<>0     0<>0   100<>100   100      100      0<>0     0<>0                              &#9474;
&#9474;< Master >Headphon   PCM     Front   Front Mi Front Mi Surround  Center    LFE      Line   Line Boo Auto-Mut Channel  Loopback &#9474;
&#9474;

---

### Post by n8mills on 2023-04-04
Of further note:

```
me@me-comp:~$ wpctl status
PipeWire 'pipewire-0' [0.3.48, me@me-comp, cookie:3785901275]
 &#9492;&#9472; Clients:
        31. WirePlumber                         [0.3.48, n8@n8-CM1735, pid:1660]
        32. WirePlumber [export]                [0.3.48, n8@n8-CM1735, pid:1660]
        36. pipewire                            [0.3.48, n8@n8-CM1735, pid:1661]
        45. GNOME Shell Volume Control          [0.3.48, n8@n8-CM1735, pid:1983]
        46. GNOME Volume Control Media Keys     [0.3.48, n8@n8-CM1735, pid:2216]
        47. xdg-desktop-portal                  [0.3.48, n8@n8-CM1735, pid:2546]
        48. KodiDriver                          [0.3.48, n8@n8-CM1735, pid:2698]
        49. VLC media player (LibVLC 3.0.18)    [0.3.48, n8@n8-CM1735, pid:15151]
        55. gnome-shell                         [0.3.48, n8@n8-CM1735, pid:1983]
        56. Brave input                         [0.3.48, n8@n8-CM1735, pid:4589]
        57. GNOME Settings                      [0.3.48, n8@n8-CM1735, pid:4801]
        65. Mutter                              [0.3.48, n8@n8-CM1735, pid:1983]
        71. wpctl                               [0.3.48, n8@n8-CM1735, pid:32240]


Audio
 &#9500;&#9472; Devices:
 &#9474;      44. Built-in Audio                      [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   35. Dummy Output                        [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        51. VLC media player (LibVLC 3.0.18)                            
             50. output_FL       > Dummy Output:playback_FL
             54. output_FR       > Dummy Output:playback_FR
        58. GNOME Settings                                              
             59. input_FL        < Dummy Output:monitor_FL
             60. monitor_FL     
             61. input_FR        < Dummy Output:monitor_FR
             62. monitor_FR 
```

---

### Post by #&amp;thj^% on 2023-04-04
Interesting still Dummy's, I'll be back, Diner Time. ;)

---

### Post by n8mills on 2023-04-04
User "dimares" on that git post last week commented that they did everything in the instructions and HDMI not working, this is also my experience.

---

### Post by #&amp;thj^% on 2023-04-05
I don't  think  "dimares"  was working with your hardware, trust me I know how frustrating this is for you, as tester I find myself at Epic levels of frustration.
If your still around will you show me this:
```
cat /etc/modprobe.d/alsa-base.conf

```
and look for a line like "options snd-hda-intel model=*****"
Pleas use Code Tags for this one, when pasting back.

---

### Post by n8mills on 2023-04-05
You might be onto something, there is no there is no "hda" text

---

### Post by n8mills on 2023-04-06
OK I did a whole fresh clean install and before doing any updates even I did the steps in the GIT article, and now I can see "HDMI/Displayport - Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon 7000 Series]", so that does work.  Let me go and do my Media Player and update installs and see what happens.

---

### Post by n8mills on 2023-04-06
Aaaaaand it's gone again.  And all I did was install Kodi

---

### Post by #&amp;thj^% on 2023-04-06
Please file a bug-report on your soundcard "Realtek ALC887-VD F2" and alsa.
If you will show me that file I asked to see there may be a workaround, until they fix this. 
```
cat /etc/modprobe.d/alsa-base.conf
```
There has been reports of Alsa not having a good priority for starting your card

---

### Post by n8mills on 2023-04-06
I appreciate your help!

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

Looks like my driver is once again missing from the file.  Adding it didn't fix before but I'll attempt that.

---

### Post by DuckHook on 2023-04-07
It appears that you are using AMD graphics card. Are you trying to output to HDMI audio? If so, the latest kernels break HDMI output for AMD and this has not yet been fixed.

There are two workarounds:

[LIST=1]
[*]Use system audio (either USB or MOBO audio if you have that)
[*]Pin the last functional kernel (5.19.0-32-generic) and make sure you boot from that one instead of anything newer.
[/LIST]
If you are not using HDMI, then ignore the above instructions as your problems arise from a different cause.

---

### Post by n8mills on 2023-05-01
Yes, I'm using HDMI for my audio.  This is embarrassingly bad for Ubuntu.  I've reverted back to using Windows because I haven't had the time to screw around with Ubuntu.

Maybe I'll try Mint instead.

---

