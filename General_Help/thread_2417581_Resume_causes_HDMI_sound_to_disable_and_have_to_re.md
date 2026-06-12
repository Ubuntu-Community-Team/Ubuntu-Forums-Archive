---
title: "Resume causes HDMI sound to disable and have to restart to get sound"
date: 2019-04-24
forum: General Help
---

### Post by richard378 on 2019-04-24
I am running Ubuntu 18.04.02 LTS, I have NVIDIA GTX 970 with latest drivers-418 from PPA HDMI display. I have resume working. When I resume after suspend the HDMI sound is not selectable under sound in settings. It has the default motherboard sound selected, and it can't be unselected. The option shows HDMI sound it available but it can't be selected. When I restart the computer, the HDMI sound is automatically selected as the default option. Tried pulseaudio and it did not work. Any suggestions?
Edit... there is a but report [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1718927](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1718927) but this seams to be a intermitant problem for me. It was working with some problems that it could be manually selected. Then it stoped working. I don't know why.
Edit... Now it is working again.  For a while it was difficult to select and was unselected automaticly.  Then it stopped working.  Now it is working normal again.  I don't know how to troubleshoot this or if it was just a fluke.

---

### Post by #&amp;thj^% on 2019-04-24
Ubuntu and pulseaudio have always been buggy here; but this "usually" works:
```
pulseaudio -k
```
You may have to wait a few seconds to get PulseAudio to re spawn, and if it won't on it's own try:
Check if any pulseaudio instance is running:
```

pulseaudio --check
```

It normally prints no output, just exit code. 0 means running. Mine was not running, so I just advanced to step 3.

If any instance is running:
```

pulseaudio -k

```
Finally, start pulseaudio again as a daemon:
```

pulseaudio -D
```
If more information is needed then use:
```
**pulseaudio -vvvv**
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 12.2
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fdebug-prefix-map=/build/pulseaudio-m5u9Lu/pulseaudio-12.2=. -fstack-protector-strong -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
D: [pulseaudio] main.c: Running on host: Linux x86_64 5.1.0-050100rc2-lowlatency #201903242231 SMP PREEMPT Sun Mar 24 22:36:51 UTC 2019
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is 9xxxxxxxxxxxxxxxxc9d.(Sniped by user)
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/me/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-12.2/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

```

---

