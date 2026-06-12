---
title: "PulseAudio Without SoundCard how to redirect sound to stream ffmpeg"
date: 2014-03-06
forum: General Help
---

### Post by jpowers718 on 2014-03-06
I have a VPS which is ran on a OpenVZ, which obviously doesn't have any sound cards installed, I know this is possible because I've seen it done before but the person refuses to tell me how it's done not to interfere with his business. 

I can't do commands such as

```

[root@website tmp]# modprobe snd-dummy
WARNING: Error inserting snd (/lib/modules/2.6.32-042stab083.2/updates/alsa/acor e/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.32-042stab083.2/updates/als a/acore/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_pcm (/lib/modules/2.6.32-042stab083.2/updates/alsa/ acore/snd-pcm.ko): Operation not permitted
FATAL: Error inserting snd_dummy (/lib/modules/2.6.32-042stab083.2/updates/alsa/ drivers/snd-dummy.ko): Operation not permitted

```
So I can't load up the snd-dummy sound card driver.


```
[root@website tmp]# aplay -l
aplay: device_list:256: no soundcards found...

```

```
[root@website tmp]# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)

```




But I did manage to install pavucontrol in my GNOME desktop when I run a application which uses SDL DirectMedia Layer and I see the slider in the Playback moving so sound is coming in without any sound card but it's redirected to [FONT=Consolas]<auto_null.monitor>

[SIZE=3]Maybe I don't even need to use the sound server PulseAudio and just redirect SDL DirectMedia Layer straight into ffmpeg somehow if that is possible, all I care about is that one SDL DirectMedia Layer, I don't need other System sounds/Mics etc..[/SIZE]

[/FONT]Here is what happens when I run this command for PulseAudio

```

[removed@removed ~]$ pacmd list-source-outputs
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 source outputs(s) available.
    index: 0
    driver: <protocol-native.c>
    flags: DONT_MOVE 
    state: RUNNING
    source: 0 <auto_null.monitor>
    current latency: 3.08 ms
    requested latency: 20.00 ms
    sample spec: float32le 1ch 25Hz
    channel map: mono
                 Mono
    resample method: peaks
    owner module: 6
    client: 4 <PulseAudio Volume Control>
    properties:
        media.name = "Peak detect"
        application.name = "PulseAudio Volume Control"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        application.id = "org.PulseAudio.pavucontrol"
        application.icon_name = "audio-card"
        application.version = "0.9.10"
        application.process.id = "997"
        application.process.user = "removed_for_ubuntuforums(wasn't root)"
        application.process.host = "removed_for_ubuntuforums"
        application.process.binary = "pavucontrol"
        window.x11.display = ":1.0"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "27be3273f5d5332051ccdc3100000002"
        application.process.session_id = "27be3273f5d5332051ccdc3100000002-1394085585.776225-694791372"
        module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"
    index: 1
    driver: <protocol-native.c>
    flags: DONT_MOVE 
    state: RUNNING
    source: 0 <auto_null.monitor>
    current latency: 3.11 ms
    requested latency: 20.00 ms
    sample spec: float32le 1ch 25Hz
    channel map: mono
                 Mono
    resample method: peaks
    owner module: 6
    client: 4 <PulseAudio Volume Control>
    direct on input: 2
    properties:
        media.name = "Peak detect"
        application.name = "PulseAudio Volume Control"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "16"
        application.id = "org.PulseAudio.pavucontrol"
        application.icon_name = "audio-card"
        application.version = "0.9.10"
        application.process.id = "997"
        application.process.user = "removed_for_ubuntuforums(wasn't root)"
        application.process.host = "removed_for_ubuntuforums"
        application.process.binary = "pavucontrol"
        window.x11.display = ":1.0"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "27be3273f5d5332051ccdc3100000002"
        application.process.session_id = "27be3273f5d5332051ccdc3100000002-1394085585.776225-694791372"
        module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"


```

Here is the PulseAudio sinks command

```

>>> [removed@removed~]$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 sink(s) available.
  * index: 0
	name: <auto_null>
	driver: <module-null-sink.c>
	flags: DECIBEL_VOLUME LATENCY FLAT_VOLUME DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: 
	priority: 1000
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 16.60 ms
	max request: 3 KiB
	max rewind: 3 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 3
	configured latency: 20.00 ms; range is 0.50 .. 10000.00 ms
	module: 9
	properties:
		device.description = "Dummy Output"
		device.class = "abstract"
		device.icon_name = "audio-card"

```

[COLOR=#333333][FONT=Helvetica Neue]Inside my PulseAudio Volume Control 
[/FONT][/COLOR][IMG]http://i.stack.imgur.com/kL5sz.png[/IMG]

Here is what I get from ffmpeg when I attempt to stream the video and sound (just video alone streams wonderfully)
[IMG]http://i.stack.imgur.com/6aJkE.png[/IMG]

---

