---
title: "NO Sound. Sound indicator shows me only &quot;dummy output&quot;"
date: 2013-08-08
forum: General Help
---

### Post by MK567 on 2013-08-08
After upgrading to 13.10 theres no sound anymore.

In sound indicator menu I see only "**Dummy output**" device.

Laptop soundcard, intel-hda:
**00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)**

Digital-to-analog converter should be:
**Realtek ALC269VB**

Alsa-script log is added with file alsa-info.txt.

Any ideas?

---

### Post by gordintoronto on 2013-08-08
In my experience, no sound is due to sound being muted 90% of the time. What program are you running which should produce sound? What brand and model of computer? (Volume control keys on the keyboard? Built-in speakers or earphones?)

I assume you meant the "Sound Settings" menu, looking at the output tab.

---

### Post by Yellow Pasque on 2013-08-09
Try resetting pulseaudio user configuration:
```
rm -r ~/.config/pulse; pulseaudio -k
```
If that doesn't work, make a verbose log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by MK567 on 2013-08-09
[**[COLOR=#000000]gordintoronto:[/COLOR]**]("http://ubuntuforums.org/member.php?u=507940") Problem here is not muted device. Problem is there is NO sound device in "Sound Settings" menu, only "Dummy device" is there.

[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"): reseting didn't change nothing.

```

$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server

```

```

$ aplay -l
aplay: device_list:268: no soundcards found...

```

```

$ ls -l /dev/snd/
drwxr-xr-x 2 root root       60 aug    9 16:13 by-path
crw-rw---- 1 root audio 116,  7 aug    9 16:13 controlC0
crw-rw---- 1 root audio 116,  6 aug    9 16:13 hwC0D0
crw-rw---- 1 root audio 116,  5 aug    9 16:13 hwC0D3
crw-rw---- 1 root audio 116,  4 aug    9 16:13 pcmC0D0c
crw-rw---- 1 root audio 116,  3 aug    9 16:13 pcmC0D0p
crw-rw---- 1 root audio 116,  2 aug    9 16:13 pcmC0D3p
crw-rw---- 1 root audio 116,  1 aug    9 16:13 seq
crw-rw---- 1 root audio 116, 33 aug    9 16:13 timer

```


Pulseaudio logfile:
```

(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.033|   0.032) I: [pulseaudio] core-util.c: Failed to acquire high-priority scheduling: Permission denied
(   0.033|   0.000) I: [pulseaudio] main.c: This is PulseAudio 4.0
(   0.033|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.033|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
(   0.033|   0.000) D: [pulseaudio] main.c: Running on host: Linux x86_64 3.11.0-031100rc4-generic #201308041735 SMP Sun Aug 4 21:36:46 UTC 2013
(   0.033|   0.000) D: [pulseaudio] main.c: Found 4 CPUs.
(   0.033|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.033|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.033|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.033|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.033|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.033|   0.000) D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
(   0.033|   0.000) I: [pulseaudio] main.c: Machine ID is c7cfd7b34b87533d898223bb512794fe.
(   0.033|   0.000) I: [pulseaudio] main.c: Using runtime directory /home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-runtime.
(   0.033|   0.000) I: [pulseaudio] main.c: Using state directory /home/anari/.pulse.
(   0.033|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
(   0.033|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.033|   0.000) I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
(   0.034|   0.000) D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65472
(   0.034|   0.000) I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
(   0.034|   0.000) I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.034|   0.000) I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
(   0.034|   0.000) I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.034|   0.000) I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
(   0.034|   0.000) I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.034|   0.000) I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
(   0.035|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-device-volumes.tdb'
(   0.035|   0.000) I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-device-volumes'.
(   0.035|   0.000) I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
(   0.035|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-stream-volumes.tdb'
(   0.035|   0.000) I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-stream-volumes'.
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry2
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry3
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry4
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry5
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry6
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry7
(   0.036|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry8
(   0.036|   0.000) I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
(   0.036|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-card-database.tdb'
(   0.036|   0.000) I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/anari/.pulse/c7cfd7b34b87533d898223bb512794fe-card-database'.
(   0.036|   0.000) I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
(   0.037|   0.000) I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
(   0.037|   0.000) I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #4; argument: "").
(   0.037|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-udev-detect.so': success
(   0.038|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: no
(   0.038|   0.000) I: [pulseaudio] module-udev-detect.c: Found 1 cards.
(   0.038|   0.000) I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #5; argument: "use_ucm=0").
(   0.038|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-jackdbus-detect.so': failure
(   0.038|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-bluetooth-policy.so': failure
(   0.038|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-bluetooth-discover.so': failure
(   0.038|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-esound-protocol-unix.so': failure
(   0.039|   0.000) I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
(   0.039|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-gconf.so': failure
(   0.039|   0.000) I: [pulseaudio] module-default-device-restore.c: Saved default sink 'auto_null' not existent, not restoring default sink setting.
(   0.039|   0.000) I: [pulseaudio] module-default-device-restore.c: Saved default source 'auto_null.monitor' not existent, not restoring default source setting.
(   0.039|   0.000) I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
(   0.039|   0.000) I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
(   0.039|   0.000) D: [pulseaudio] module-always-sink.c: Autoloading null-sink as no other sinks detected.
(   0.040|   0.000) I: [pulseaudio] module-device-restore.c: Restoring volume for sink auto_null.
(   0.040|   0.000) I: [pulseaudio] module-device-restore.c: Restored volume: 0: 100% 1: 100%
(   0.040|   0.000) I: [pulseaudio] module-device-restore.c: Restoring mute state for sink auto_null.
(   0.040|   0.000) I: [pulseaudio] sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.040|   0.000) I: [pulseaudio] sink.c:     device.description = "Dummy Output"
(   0.040|   0.000) I: [pulseaudio] sink.c:     device.class = "abstract"
(   0.040|   0.000) I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
(   0.040|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.040|   0.000) I: [pulseaudio] source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.040|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Dummy Output"
(   0.040|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(   0.040|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
(   0.040|   0.000) D: [null-sink] module-null-sink.c: Thread starting up
(   0.040|   0.000) D: [pulseaudio] module-device-restore.c: Could not set format on sink auto_null
(   0.040|   0.000) I: [pulseaudio] module.c: Loaded "module-null-sink" (index: #9; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
(   0.040|   0.000) I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #10; argument: "").
(   0.041|   0.000) I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #11; argument: "").
(   0.041|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(   0.041|   0.000) I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #12; argument: "").
(   0.041|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-console-kit.so': failure
(   0.041|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-systemd-login.so': success
(   0.041|   0.000) I: [pulseaudio] module.c: Loaded "module-systemd-login" (index: #13; argument: "").
(   0.041|   0.000) I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
(   0.042|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #15; argument: "").
(   0.042|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #16; argument: "").
(   0.042|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-dbus-protocol.so': success
(   0.042|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Memstats added for object /org/pulseaudio/core1/memstats
(   0.042|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device added for object /org/pulseaudio/core1/sink0
(   0.042|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Sink added for object /org/pulseaudio/core1/sink0
(   0.042|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device added for object /org/pulseaudio/core1/source0
(   0.042|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Source added for object /org/pulseaudio/core1/source0
(   0.042|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module0
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module1
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module2
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module3
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module4
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module5
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module6
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module7
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module8
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module9
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module10
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module11
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module12
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module13
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module14
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module15
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module16
(   0.043|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1 added for object /org/pulseaudio/core1
(   0.043|   0.000) I: [pulseaudio] module.c: Loaded "module-dbus-protocol" (index: #17; argument: "").
(   0.044|   0.000) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus session bus 8c543e1352cdbad9a6baa2645204eb29 as :1.82
(   0.044|   0.000) D: [pulseaudio] main.c: Got org.PulseAudio1!
(   0.045|   0.000) D: [pulseaudio] main.c: Got org.pulseaudio.Server!
(   0.045|   0.000) I: [pulseaudio] main.c: Daemon startup complete.
(   0.045|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module added for object /org/pulseaudio/core1/module17
(   0.045|   0.000) I: [pulseaudio] client.c: Created 0 "Native client (UNIX socket client)"
(   0.045|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client0
(   0.045|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(   0.045|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.045|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   0.045|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   0.046|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
(   5.047|   5.001) I: [pulseaudio] module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
(   5.047|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink auto_null is 0x0004, suspending
(   5.047|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   9.336|   4.289) I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
(   9.336|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client1
(   9.602|   0.265) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(   9.602|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   9.602|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   9.602|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   9.606|   0.003) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-control-center
(   9.606|   0.000) D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/gnome-control-center.desktop.
(  11.682|   2.076) I: [pulseaudio] client.c: Freed 1 "GNOME Volume Control Dialog"
(  11.682|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  11.682|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client1
(  17.613|   5.931) I: [pulseaudio] client.c: Created 2 "Native client (UNIX socket client)"
(  17.614|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client2
(  17.614|   0.000) I: [pulseaudio] client.c: Freed 2 "Native client (UNIX socket client)"
(  17.614|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  17.614|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client2
(  17.619|   0.005) I: [pulseaudio] client.c: Created 3 "Native client (UNIX socket client)"
(  17.620|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client added for object /org/pulseaudio/core1/client3
(  17.620|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
(  17.620|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  17.620|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(  17.620|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(  17.620|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for deadbeef
(  17.620|   0.000) D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/deadbeef.desktop.
(  17.621|   0.000) D: [pulseaudio] module-intended-roles.c: Not setting device for stream ALSA Playback, because it lacks role.
(  17.621|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes busy, resuming.
(  17.621|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink auto_null is 0x0000, resuming
(  17.621|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(  17.621|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(  17.621|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(  17.621|   0.000) I: [pulseaudio] sink-input.c: Created input 0 "ALSA Playback" on auto_null with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     media.name = "ALSA Playback"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.name = "ALSA plug-in [deadbeef]"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.version = "28"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.process.id = "29041"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.process.user = "anari"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.process.host = "anari-vosto"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.process.binary = "deadbeef"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.language = "et_EE.UTF-8"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     window.x11.display = ":0"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.process.machine_id = "c7cfd7b34b87533d898223bb512794fe"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     application.icon_name = "deadbeef"
(  17.621|   0.000) I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:ALSA plug-in [deadbeef]"
(  17.621|   0.000) I: [pulseaudio] protocol-native.c: Requested tlength=185,76 ms, minreq=23,22 ms
(  17.621|   0.000) D: [pulseaudio] protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
(  17.621|   0.000) D: [pulseaudio] protocol-native.c: Requested latency=23,22 ms, Received latency=23,22 ms
(  17.621|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=32768, base=4, prebuf=4096, minreq=4096 maxrewind=0
(  17.621|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=32768, base=4, prebuf=4096, minreq=4096 maxrewind=0
(  17.621|   0.000) I: [pulseaudio] protocol-native.c: Final latency 208,98 ms = 139,32 ms + 2*23,22 ms + 23,22 ms
(  17.621|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(  17.621|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream added for object /org/pulseaudio/core1/playback_stream0
(  17.622|   0.000) D: [null-sink] module-null-sink.c: Requested to rewind 352800 bytes.
(  17.622|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(  17.622|   0.000) D: [null-sink] sink.c: Processing rewind...
(  17.622|   0.000) D: [null-sink] source.c: Processing rewind...
(  17.622|   0.000) D: [null-sink] module-null-sink.c: Rewound 3952 bytes.
(  17.622|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(  17.622|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  17.622|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream removed from object /org/pulseaudio/core1/playback_stream0
(  17.622|   0.000) I: [pulseaudio] sink-input.c: Freeing input 0 "ALSA Playback"
(  17.623|   0.000) D: [pulseaudio] module-intended-roles.c: Not setting device for stream ALSA Playback, because it lacks role.
(  17.623|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes busy, resuming.
(  17.623|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(  17.623|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(  17.623|   0.000) I: [pulseaudio] sink-input.c: Created input 1 "ALSA Playback" on auto_null with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     media.name = "ALSA Playback"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.name = "ALSA plug-in [deadbeef]"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.peer = "UNIX socket client"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     native-protocol.version = "28"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.process.id = "29041"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.process.user = "anari"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.process.host = "anari-vosto"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.process.binary = "deadbeef"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.language = "et_EE.UTF-8"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     window.x11.display = ":0"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.process.machine_id = "c7cfd7b34b87533d898223bb512794fe"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     application.icon_name = "deadbeef"
(  17.623|   0.000) I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:ALSA plug-in [deadbeef]"
(  17.623|   0.000) I: [pulseaudio] protocol-native.c: Requested tlength=185,76 ms, minreq=23,22 ms
(  17.623|   0.000) D: [pulseaudio] protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
(  17.623|   0.000) D: [pulseaudio] protocol-native.c: Requested latency=23,22 ms, Received latency=23,22 ms
(  17.623|   0.000) D: [pulseaudio] memblockq.c: memblockq requested: maxlength=4194304, tlength=32768, base=4, prebuf=28672, minreq=4096 maxrewind=0
(  17.623|   0.000) D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=4194304, tlength=32768, base=4, prebuf=28672, minreq=4096 maxrewind=0
(  17.623|   0.000) I: [pulseaudio] protocol-native.c: Final latency 208,98 ms = 139,32 ms + 2*23,22 ms + 23,22 ms
(  17.623|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream added for object /org/pulseaudio/core1/playback_stream1
(  17.635|   0.011) D: [null-sink] protocol-native.c: Requesting rewind due to end of underrun.
(  17.635|   0.000) D: [null-sink] module-null-sink.c: Requested to rewind 4092 bytes.
(  17.635|   0.000) D: [null-sink] sink.c: Processing rewind...
(  17.635|   0.000) D: [null-sink] sink-input.c: Have to rewind 2012 bytes on render memblockq.
(  17.635|   0.000) D: [null-sink] source.c: Processing rewind...
(  17.635|   0.000) D: [null-sink] module-null-sink.c: Rewound 2012 bytes.
(  20.135|   2.499) D: [null-sink] sink-input.c: Requesting rewind due to corking
(  20.135|   0.000) D: [null-sink] module-null-sink.c: Requested to rewind 4092 bytes.
(  20.135|   0.000) D: [null-sink] sink.c: Processing rewind...
(  20.135|   0.000) D: [null-sink] sink-input.c: Have to rewind 1364 bytes on render memblockq.
(  20.135|   0.000) D: [null-sink] sink-input.c: Have to rewind 1364 bytes on implementor.
(  20.135|   0.000) D: [null-sink] source.c: Processing rewind...
(  20.135|   0.000) D: [null-sink] module-null-sink.c: Rewound 1364 bytes.
(  20.135|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(  20.156|   0.020) D: [null-sink] module-null-sink.c: Requested to rewind 352800 bytes.
(  20.156|   0.000) D: [null-sink] sink.c: Processing rewind...
(  20.156|   0.000) D: [null-sink] source.c: Processing rewind...
(  20.156|   0.000) D: [null-sink] module-null-sink.c: Rewound 400 bytes.
(  20.156|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(  20.156|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  20.156|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Stream removed from object /org/pulseaudio/core1/playback_stream1
(  20.156|   0.000) I: [pulseaudio] sink-input.c: Freeing input 1 "ALSA Playback"
(  20.157|   0.000) I: [pulseaudio] client.c: Freed 3 "ALSA plug-in [deadbeef]"
(  20.157|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  20.157|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client3
(  25.161|   5.004) I: [pulseaudio] module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
(  25.161|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink auto_null is 0x0004, suspending
(  25.161|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(  30.497|   5.335) I: [pulseaudio] main.c: Got signal SIGINT.
(  30.497|   0.000) I: [pulseaudio] main.c: Exiting.
(  30.497|   0.000) I: [pulseaudio] main.c: Daemon shutdown initiated.
(  30.497|   0.000) I: [pulseaudio] module.c: Unloading "module-dbus-protocol" (index: #17).
(  30.497|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1 removed from object /org/pulseaudio/core1
(  30.497|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device removed from object /org/pulseaudio/core1/sink0
(  30.497|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Sink removed from object /org/pulseaudio/core1/sink0
(  30.497|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Device removed from object /org/pulseaudio/core1/source0
(  30.497|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Source removed from object /org/pulseaudio/core1/source0
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module0
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module1
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module2
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module3
(  30.498|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module4
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module5
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module6
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module7
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module8
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module9
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module10
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module11
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module12
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module13
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module14
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module15
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module16
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Module removed from object /org/pulseaudio/core1/module17
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Client removed from object /org/pulseaudio/core1/client0
(  30.498|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Memstats removed from object /org/pulseaudio/core1/memstats
(  30.498|   0.000) I: [pulseaudio] module.c: Unloaded "module-dbus-protocol" (index: #17).
(  30.498|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-apply" (index: #16).
(  30.498|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-apply" (index: #16).
(  30.498|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-heuristics" (index: #15).
(  30.499|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-heuristics" (index: #15).
(  30.499|   0.000) I: [pulseaudio] module.c: Unloading "module-position-event-sounds" (index: #14).
(  30.499|   0.000) I: [pulseaudio] module.c: Unloaded "module-position-event-sounds" (index: #14).
(  30.499|   0.000) I: [pulseaudio] module.c: Unloading "module-systemd-login" (index: #13).
(  30.500|   0.001) I: [pulseaudio] module.c: Unloaded "module-systemd-login" (index: #13).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-suspend-on-idle" (index: #12).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-suspend-on-idle" (index: #12).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-intended-roles" (index: #11).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-intended-roles" (index: #11).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-always-sink" (index: #10).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-always-sink" (index: #10).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-null-sink" (index: #9).
(  30.500|   0.000) D: [pulseaudio] module-rescue-streams.c: No sink inputs to move away.
(  30.500|   0.000) D: [pulseaudio] module-rescue-streams.c: No source outputs to move away.
(  30.500|   0.000) D: [null-sink] module-null-sink.c: Thread shutting down
(  30.500|   0.000) I: [pulseaudio] sink.c: Freeing sink 0 "auto_null"
(  30.500|   0.000) I: [pulseaudio] source.c: Freeing source 0 "auto_null.monitor"
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-null-sink" (index: #9).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-rescue-streams" (index: #8).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-rescue-streams" (index: #8).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-default-device-restore" (index: #7).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-default-device-restore" (index: #7).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #6).
(  30.500|   0.000) I: [pulseaudio] client.c: Freed 0 "GNOME Volume Control Media Keys"
(  30.500|   0.000) I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #6).
(  30.500|   0.000) I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #5).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #5).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #4).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #4).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 removed from object /org/pulseaudio/stream_restore1
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry0
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry1
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry2
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry3
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry4
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry5
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry6
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry7
(  30.501|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry8
(  30.501|   0.000) I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
(  30.501|   0.000) I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
(  30.501|   0.000) I: [pulseaudio] main.c: Daemon terminated.

```

---

### Post by SweetAurora on 2013-08-09
Try this, it looks like a bug with this card and the snd-hda-intel driver
```
sudo -i /etc/modprobe.d/alsa-base.conf
```
then go to the very bottom of the document and make a space there and type:
```
options snd-hda-intel model=auto
```
save and then reboot.

---

### Post by Yellow Pasque on 2013-08-09
The problem is your custom /etc/asound.conf . Remove that file and reboot. Better?
```
!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

pcm.!default {
	type hw
	card 0
}

ctl.!default {
	type hw           
	card 0
}

```

---

### Post by MK567 on 2013-08-10
[**[COLOR=#000000]kitsuneinari78[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841591"): After adding "options snd-hda-intel model=auto" there was no change.
[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"): After removing my "/etc/asound.conf" I am able to get this information but still no usable sound in my system.

If I run "aplay -l" theres no devices. "aplay: device_list:268: no soundcards found..."

If I run "sudo aplay -l" i see this:
```

$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Is this some kind of permissions issue?

Alsascript in sudo mode:
```

!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)



!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xd0700000 irq 49'
  Mixer name    : 'Intel CougarPoint HDMI'
  Components    : 'HDA:10ec0269,102804d9,00100100 HDA:80862805,80860101,00100000'
  Controls      : 28
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 60 [69%] [-20.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 19 [61%] [12.00dB] [on]
  Front Right: Capture 19 [61%] [12.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
    control.1 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 87
        value.1 87
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 87
        value.1 87
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.6 {
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.7 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.8 {
        iface MIXER
        name 'Capture Volume'
        value.0 19
        value.1 19
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.9 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.10 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3600
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.11 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3600
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.12 {
        iface MIXER
        name 'Master Playback Volume'
        value 60
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 87'
            dbmin -6525
            dbmax 0
            dbvalue.0 -2025
        }
    }
    control.13 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface CARD
        name 'Internal Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.16 {
        iface CARD
        name 'Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface CARD
        name 'Speaker Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'Beep Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.19 {
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.20 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.21 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.22 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.25 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.28 {
        iface PCM
        device 3
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write'
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
}
--endcollapse--

```

---

### Post by Yellow Pasque on 2013-08-10
Check:
```
cat /etc/group | grep audio
```

---

### Post by MK567 on 2013-08-11
```

$ cat /etc/group | grep audio
audio:x:29:pulse

```

---

### Post by MK567 on 2013-08-26
I believe I fixed it by command:

```

sudo pam-auth-update --force
```

---

