---
title: "Pulseaudio fails to load volume module (volume resets to 100% after reboot)"
date: 2016-02-29
forum: General Help
---

### Post by SepLite on 2016-02-29
Hello all,
Recently I've been having an issue where my volume resets to 100% after restarting my computer, resulting in many undesirable circumstances where a notification comes on and destroys my headphones and my ears. I have done some googling, but most of the answers were startup script "patches" that did not fix the underlying problem, which I would like/prefer to do.

Here are my pulseaudio logs:
```


I (   0.000|   0.000)  [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I (   0.000|   0.000)  [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D (   0.000|   0.000)  [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D (   0.002|   0.002)  [pulseaudio] core-util.c: RealtimeKit worked.
I (   0.002|   0.000)  [pulseaudio] core-util.c: Successfully gained nice level -11.
I (   0.002|   0.000)  [pulseaudio] main.c: This is PulseAudio 4.0
D (   0.002|   0.000)  [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D (   0.002|   0.000)  [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D (   0.002|   0.000)  [pulseaudio] main.c: Running on host: Linux x86_64 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016
D (   0.002|   0.000)  [pulseaudio] main.c: Found 4 CPUs.
I (   0.002|   0.000)  [pulseaudio] main.c: Page size is 4096 bytes
D (   0.002|   0.000)  [pulseaudio] main.c: Compiled with Valgrind support: no
D (   0.002|   0.000)  [pulseaudio] main.c: Running in valgrind mode: no
D (   0.002|   0.000)  [pulseaudio] main.c: Running in VM: no
D (   0.002|   0.000)  [pulseaudio] main.c: Optimized build: yes
D (   0.002|   0.000)  [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I (   0.002|   0.000)  [pulseaudio] main.c: Machine ID is 04a41ec4d0f78cfbfa460e58561f10c2.
I (   0.002|   0.000)  [pulseaudio] main.c: Session ID is c1.
I (   0.002|   0.000)  [pulseaudio] main.c: Using runtime directory /run/user/112/pulse.
I (   0.002|   0.000)  [pulseaudio] main.c: Using state directory /var/lib/lightdm/.config/pulse.
I (   0.002|   0.000)  [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I (   0.002|   0.000)  [pulseaudio] main.c: Running in system mode: no
I (   0.002|   0.000)  [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
D (   0.002|   0.000)  [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
I (   0.002|   0.000)  [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
I (   0.002|   0.000)  [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
I (   0.002|   0.000)  [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
I (   0.002|   0.000)  [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
I (   0.002|   0.000)  [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
I (   0.002|   0.000)  [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
I (   0.002|   0.000)  [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
D (   0.003|   0.000)  [pulseaudio] database-tdb.c: Opened TDB database '/var/lib/lightdm/.config/pulse/04a41ec4d0f78cfbfa460e58561f10c2-device-volumes.tdb'
I (   0.003|   0.000)  [pulseaudio] module-device-restore.c: Successfully opened database file '/var/lib/lightdm/.config/pulse/04a41ec4d0f78cfbfa460e58561f10c2-device-volumes'.
I (   0.003|   0.000)  [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
D (   0.003|   0.000)  [pulseaudio] database-tdb.c: Opened TDB database '/var/lib/lightdm/.config/pulse/04a41ec4d0f78cfbfa460e58561f10c2-stream-volumes.tdb'
I (   0.003|   0.000)  [pulseaudio] module-stream-restore.c: Successfully opened database file '/var/lib/lightdm/.config/pulse/04a41ec4d0f78cfbfa460e58561f10c2-stream-volumes'.
D (   0.003|   0.000)  [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
D (   0.003|   0.000)  [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
I (   0.003|   0.000)  [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D (   0.003|   0.000)  [pulseaudio] database-tdb.c: Opened TDB database '/var/lib/lightdm/.config/pulse/04a41ec4d0f78cfbfa460e58561f10c2-card-database.tdb'
I (   0.003|   0.000)  [pulseaudio] module-card-restore.c: Successfully opened database file '/var/lib/lightdm/.config/pulse/04a41ec4d0f78cfbfa460e58561f10c2-card-database'.
I (   0.003|   0.000)  [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
E (   0.004|   0.000)  [pulseaudio] ltdl-bind-now.c: Failed to open module module-volume.so: module-volume.so: cannot open shared object file: No such file or directory
E (   0.004|   0.000)  [pulseaudio] module.c: Failed to open module "module-volume".
E (   0.004|   0.000)  [pulseaudio] main.c: Module load failed.
E (   0.004|   0.000)  [pulseaudio] main.c: Failed to initialize daemon.
I (   0.004|   0.000)  [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
I (   0.004|   0.000)  [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
D (   0.004|   0.000)  [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
I (   0.004|   0.000)  [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
D (   0.004|   0.000)  [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 removed from object /org/pulseaudio/stream_restore1
D (   0.004|   0.000)  [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry0
I (   0.004|   0.000)  [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
D (   0.004|   0.000)  [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
I (   0.004|   0.000)  [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
I (   0.004|   0.000)  [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
D (   0.004|   0.000)  [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
I (   0.004|   0.000)  [pulseaudio] main.c: Daemon terminated.
E (   0.000|   0.000)  [pulseaudio] main.c: Daemon startup failed.
```

I believe the problem occurs when it says
```
E (   0.004|   0.000)  [pulseaudio] ltdl-bind-now.c: Failed to open module module-volume.so: module-volume.so: cannot open shared object file: No such file or directory
E (   0.004|   0.000)  [pulseaudio] module.c: Failed to open module "module-volume".
E (   0.004|   0.000)  [pulseaudio] main.c: Module load failed.
E (   0.004|   0.000)  [pulseaudio] main.c: Failed to initialize daemon.
```

Thanks,

---

