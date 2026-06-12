---
title: "Ubuntu 18.04 no sound"
date: 2019-02-19
forum: General Help
---

### Post by jadechessink on 2019-02-19
i have no sound in my ubuntu 18.04 install on my new asus chromebook. 

ive tried adding options snd-hda-intel model=default to my alsa conf but it still doent work. 

any ideas?

---

### Post by NM5TF on 2019-02-19
be sure to look at the ALSA mixer & volume controls to be certain nothing is muted...

or you might look at this  [https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html)

tommy

---

### Post by jadechessink on 2019-02-19
not muted, reinstalled pulse and alsa, tried everything i can think of, heres the mixer[ATTACH=CONFIG]282584[/ATTACH]

---

### Post by #&amp;thj^% on 2019-02-19
Can you also give us the return from the terminal:
```
inxi -GAz
```
mine shows as follows;
```

Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.3 driver: intel resolution: 1600x900~60Hz 
  OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile v: 4.2 Mesa 18.3.3 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k4.20.10.a-1-hardened 
```
Both ALSA and PulseAudio come with command line appliciations to print out the state of our sound system.

    PulseAudio:

   ```
pactl list
```

    ALSA:

  ```
aplay -l
```

Both will give an error if the sound system is not running.

---

### Post by jadechessink on 2019-02-19
here you are:

```
james@chromebook1:~$ inxi -GAz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Bay Trail version: 4.2 Mesa 18.2.2
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic


```

```
james@chromebook1:~$ pactl list
Module #0
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "11.1"

Module #1
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "11.1"

Module #2
    Name: module-card-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "11.1"

Module #3
    Name: module-augment-properties
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "11.1"

Module #4
    Name: module-switch-on-port-available
    Argument: 
    Usage counter: n/a
    Properties:
        

Module #5
    Name: module-switch-on-connect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Michael Terry"
        module.description = "When a sink/source is added, switch to it or conditionally switch to it"
        module.version = "11.1"

Module #6
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "11.1"

Module #7
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "11.1"

Module #9
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "11.1"

Module #10
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "11.1"

Module #11
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move its streams to the default sink/source"
        module.version = "11.1"

Module #12
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "11.1"

Module #13
    Name: module-null-sink
    Argument: sink_name=auto_null sink_properties='device.description="Dummy Output"'
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Clocked NULL sink"
        module.version = "11.1"

Module #14
    Name: module-intended-roles
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based on intended roles of devices"
        module.version = "11.1"

Module #15
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "11.1"

Module #16
    Name: module-console-kit
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each ConsoleKit session of this user"
        module.version = "11.1"

Module #17
    Name: module-systemd-login
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each login session of this user"
        module.version = "11.1"

Module #18
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "11.1"

Module #19
    Name: module-role-cork
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Mute & cork streams with certain roles while others exist"
        module.version = "11.1"

Module #20
    Name: module-filter-heuristics
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Detect when various filters are desirable"
        module.version = "11.1"

Module #21
    Name: module-filter-apply
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Load filter sinks automatically when needed"
        module.version = "11.1"

Module #27
    Name: module-x11-publish
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 credential publisher"
        module.version = "11.1"

Module #28
    Name: module-x11-bell
    Argument: display=:0 sample=bell.ogg
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 bell interceptor"
        module.version = "11.1"

Module #29
    Name: module-x11-cork-request
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Synthesize X11 media key events when cork/uncork is requested"
        module.version = "11.1"

Module #30
    Name: module-x11-xsmp
    Argument: display=:0 session_manager=local/chromebook1:@/tmp/.ICE-unix/819,unix/chromebook1:/tmp/.ICE-unix/819
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 session management"
        module.version = "11.1"

Sink #0
    State: SUSPENDED
    Name: auto_null
    Description: Dummy Output
    Driver: module-null-sink.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 13
    Mute: no
    Volume: front-left: 42590 /  65% / -11.23 dB,   front-right: 42590 /  65% / -11.23 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor Source: auto_null.monitor
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"
    Formats:
        pcm

Source #0
    State: SUSPENDED
    Name: auto_null.monitor
    Description: Monitor of Dummy Output
    Driver: module-null-sink.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 13
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: auto_null
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Dummy Output"
        device.class = "monitor"
        device.icon_name = "audio-input-microphone"
    Formats:
        pcm

Client #0
    Driver: module-systemd-login.c
    Owner Module: 17
    Properties:
        application.name = "Login Session 1"
        systemd-login.session = "1"

Client #1
    Driver: protocol-native.c
    Owner Module: 9
    Properties:
        application.name = "GNOME Shell Volume Control"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "3.28.3"
        application.process.id = "943"
        application.process.user = "james"
        application.process.host = "chromebook1"
        application.process.binary = "gnome-shell"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "83e74ca998c64abd956d4f4c42a31d27"
        application.process.session_id = "1"

Client #7
    Driver: module-x11-xsmp.c
    Owner Module: 30
    Properties:
        application.name = "XSMP Session on gnome-session as 10583b29a45f826cdc155059851057806800000008190057"
        xsmp.vendor = "gnome-session"
        xsmp.client.id = "10583b29a45f826cdc155059851057806800000008190057"

Client #8
    Driver: protocol-native.c
    Owner Module: 9
    Properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = ""
        application.process.id = "1197"
        application.process.user = "james"
        application.process.host = "chromebook1"
        application.process.binary = "gsd-media-keys"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "83e74ca998c64abd956d4f4c42a31d27"
        application.process.session_id = "1"

Client #9
    Driver: protocol-native.c
    Owner Module: 9
    Properties:
        application.name = "GNOME Volume Control Dialog"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = ""
        application.process.id = "1374"
        application.process.user = "james"
        application.process.host = "chromebook1"
        application.process.binary = "gnome-control-center"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "83e74ca998c64abd956d4f4c42a31d27"
        application.process.session_id = "1"

Client #14
    Driver: protocol-native.c
    Owner Module: 9
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.process.id = "3953"
        application.process.user = "james"
        application.process.host = "chromebook1"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "83e74ca998c64abd956d4f4c42a31d27"
        application.process.session_id = "1"

Sample #0
    Name: bell.ogg
    Sample Specification: float32le 1ch 44100Hz
    Channel Map: mono
    Volume: (invalid)
            balance 0.00
    Duration: 0.2s
    Size: 34.5 KiB
    Lazy: no
    Filename: n/a
    Properties:
        media.role = "event"
        media.name = "bell.ogg"
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.process.id = "1189"
        application.process.user = "james"
        application.process.host = "chromebook1"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "83e74ca998c64abd956d4f4c42a31d27"
        application.process.session_id = "1"

Card #0
    Name: alsa_card.pci-0000_00_1b.0
    Driver: module-alsa-card.c
    Owner Module: 7
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd0714000 irq 90"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0f04"
        device.product.name = "Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority: 5400, available: no)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority: 300, available: no)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (sinks: 1, sources: 0, priority: 300, available: no)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (sinks: 1, sources: 0, priority: 5200, available: no)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (sinks: 1, sources: 0, priority: 100, available: no)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (sinks: 1, sources: 0, priority: 100, available: no)
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
    Active Profile: off
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "video-display"
            Part of profile(s): output:hdmi-stereo, output:hdmi-surround, output:hdmi-surround71
        hdmi-output-1: HDMI / DisplayPort 2 (priority: 5800, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "video-display"
            Part of profile(s): output:hdmi-stereo-extra1, output:hdmi-surround-extra1, output:hdmi-surround71-extra1


```
```
james@chromebook1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: chtmax98090 [chtmax98090], device 0: Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: chtmax98090 [chtmax98090], device 1: Deep-Buffer Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by #&amp;thj^% on 2019-02-19
install "pavucontrol" and play around with the built-in audio controller. Switch profile to "Analog Stereo Duplex"
And a friendly reminder to use Code Tags for long outputs. :)

---

### Post by jadechessink on 2019-02-19
already tried that, unfortunately it doesnt detect any analog stereo outputs/profiles. 

only shows dummy output.

---

### Post by #&amp;thj^% on 2019-02-19
That screenshot shows me you are on the output tab, you will need to see if any other options are in the "Configuration Tab"

---

### Post by jadechessink on 2019-02-19
hard to take a screen shot of that since its a drop down, but the only options are digital and they all state unplugged.

---

### Post by #&amp;thj^% on 2019-02-19
> **jadechessink said:**
> hard to take a screen shot of that since its a drop down, but the only options are digital and they all state unplugged.

Just a bit harder is all, I use a delay for those types of shots. :)
What kind of audio cable are you using here? And what types of inputs do you show on that machine?

---

### Post by jadechessink on 2019-02-19
i actually did try delay, but it ended up deselecting it as it took the picture lol. 

this would be the built in speakers for the laptop. 

bluetooth audio works like a charm however :P

---

### Post by jadechessink on 2019-02-19
did the whole screen and it didnt deselect. 

heres that screen shot for you.

---

### Post by #&amp;thj^% on 2019-02-19
So I'm assuming then that you have a Speakers/Headphone Jack plugged in then?
EDIT: Can you just send me a link to your exact ChromeBook with the specs.

---

### Post by jadechessink on 2019-02-19
Heres the chromebook from the asus website: [https://www.asus.com/us/Laptops/ASUS_Chromebook_C300/](https://www.asus.com/us/Laptops/ASUS_Chromebook_C300/)

this isnt a plugged in device, this is the internal built in laptop speakers.

---

### Post by #&amp;thj^% on 2019-02-19
This may sound silly and just bear with me here, but are there any cables connected to any of the ports i point to in my screenshot?
BTW its good to hear that your Bluetooth device works, this is encouraging news. ;)

---

### Post by jadechessink on 2019-02-19
lol, there is no cables plugged in.

---

### Post by jadechessink on 2019-02-19
found a guide that fixed the issue i was having with my sound, followed this step by step and it fix my sound issue. 

[http://azloco.org/?q=node/273](http://azloco.org/?q=node/273)

---

### Post by reggy777 on 2019-02-20
I have spent 3 hours before find the SOLUTION! Absolutely tired! THANK YOU!

---

### Post by rmmal on 2019-08-30
the link has no solution , can u mention me the steps here ??

---

### Post by coffeecat on 2019-08-30
Back to sleep, old thread.

@rmmal, instead of necromancing an old thread marked solved, please start your own thread, detailing your problem, and not forgetting to post details of your hardware and the version of Ubuntu that you are using.

Thread closed.

---

