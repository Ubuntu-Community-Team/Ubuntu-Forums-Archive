---
title: "Suppress all messages with cvlc"
date: 2018-08-13
forum: General Help
---

### Post by raleigh3 on 2018-08-13
When I use this

```
cvlc --play-and-exit /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 2> /dev/null
```

or this

```
cvlc -q --play-and-exit /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 &> /dev/null
```

I get these irritating messages like

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 19661 [30%] [on]
  Front Right: Playback 19661 [30%] [on]

```
Any to suppress them?

---

### Post by raleigh3 on 2018-08-15
This works.

```
cvlc --play-and-exit /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3 > /dev/null 2>&1
```

---

