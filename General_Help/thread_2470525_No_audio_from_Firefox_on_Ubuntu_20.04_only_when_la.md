---
title: "No audio from Firefox on Ubuntu 20.04 only when launched from systemd"
date: 2022-01-02
forum: General Help
---

### Post by joshhawk on 2022-01-02
Just upgraded an old server from 18.04 to 20.04. Overall not a bad  experience, and 18.04 had been rock solid. However, I do have one  problem that I'm sure the community can help me with.

 I have a home automation platform running and I've created a service  with systemd to launch Firefox and play a Youtube video when a specific  MQTT message is received. This service worked great on 18.04.

 Now with 20.04, systemd runs the script, Firefox launches, but there is no audio output.

 If I manually run the same shell script that systemd runs from a  terminal command line, all works as expected and I hear Youtube audio.

 These are the only errors I see from systemctl status when systemd launches Firefox:

 ```
Jan  2 16:37:47 hawkserv mqtt-launcher.sh[53123]: [Child 53123, MediaDecoderStateMachine #1] WARNING: 7fe6096b6b50 OpenCubeb() failed to init cubeb: file /build/firefox-BVyW0E/firefox-95.0.1+build2/dom/media/AudioStream.cpp:324
Jan  2 16:37:47 hawkserv mqtt-launcher.sh[53123]: [Child 53123, MediaDecoderStateMachine #1] WARNING: Decoder=7fe6096c4d00 [OnMediaSinkAudioError]: file /build/firefox-BVyW0E/firefox-95.0.1+build2/dom/media/MediaDecoderStateMachine.cpp:4007
```

 Systemd launches Firefox with my user/group, but it seems like  there's still some kind of permission problem somewhere that isn't  allowing a systemd launched Firefox to access the pulseaudio sink.  That's my best guess, at least.

 Anyone have any ideas or tips or general direction to point me in? Thanks in advance!

---

### Post by &amp;KyT$0P# on 2022-01-02
Is the user logged in?
Any important differences in environment variables?
Are you sandboxing Firefox in one or both cases?

---

### Post by joshhawk on 2022-01-02
Yep, the user is myself. Not sandboxing Firefox in either case. Can't imagine the env vars would be any different. 

I am not a pulseaudio expert, and I did have to delete my pulseaudio config (in ~/.config/pulse/) in order to get any audio working after upgrading. 

But I can launch the same shell script that systemd launches as my user in an open terminal, and I get audio. 

Just not sure where to even begin looking, since I don't have meaningful error messages anywhere...

---

### Post by joshhawk on 2022-01-02
Followed the pulseaudio hunch, and that seemed to be the issue. I came across this, which solved my issue:

[https://newbedev.com/pulseaudio-as-system-wide-systemd-service](https://newbedev.com/pulseaudio-as-system-wide-systemd-service)

---

