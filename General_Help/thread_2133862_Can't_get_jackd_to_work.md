---
title: "Can't get jackd to work"
date: 2013-04-09
forum: General Help
---

### Post by kahrkunne on 2013-04-09
```

  
[COLOR=#999999]17:08:59.055 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:08:59.056 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:08:59.072 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:08:59.078 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]17:08:59.087 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]17:09:00.281 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Tue Apr  9 17:09:00 2013: Starting jack server...
 Tue Apr  9 17:09:00 2013: JACK server starting in realtime mode with priority 10
 Tue Apr  9 17:09:00 2013: [1m[31mERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[0m
 Tue Apr  9 17:09:00 2013: control device hw:0
 Tue Apr  9 17:09:00 2013: control device hw:0
 Tue Apr  9 17:09:00 2013: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
 Tue Apr  9 17:09:00 2013: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Tue Apr  9 17:09:00 2013: [1m[31mERROR: Cannot initialize driver[0m
 Tue Apr  9 17:09:00 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
 Tue Apr  9 17:09:00 2013: [1m[31mERROR: Failed to open server[0m
 Tue Apr  9 17:09:02 2013: Saving settings to "/home/kahr/.config/jack/conf.xml" ...
 [COLOR=#ff0000]17:09:04.948 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started

```

This is the error that I get when starting jack through qjackctl.
I tried disabling realtime, picking a different audio device, and reinstalling jack.
I made sure I'm a member of the audio group and that pulseaudio isn't running.
It will actually run if I go to setup -> misc and disable the D-Bus, but it won't actually work.

Anyone can help me?

---

