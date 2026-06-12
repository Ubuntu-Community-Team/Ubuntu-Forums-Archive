---
title: "Get list of files used by an application"
date: 2016-07-22
forum: General Help
---

### Post by istvan5 on 2016-07-22
Hi !

Is there any possibility to find out which files (with path) are used by an application when you start it ? Maybe realtime ?


thx

---

### Post by steeldriver on 2016-07-22
You could background the process immediately, capture the PID, and feed that to lsof e.g.

```

$ xeyes 2>/dev/null & lsof -p $!
[1] 10144
COMMAND   PID    USER   FD   TYPE             DEVICE SIZE/OFF     NODE NAME
xeyes   10144 steeldriver  cwd    DIR              252,0     4096  1835249 /home/steeldriver
xeyes   10144 steeldriver  rtd    DIR              252,0     4096        2 /
xeyes   10144 steeldriver  txt    REG              252,0    20944  3016042 /usr/bin/xeyes
xeyes   10144 steeldriver  mem    REG              252,0  7216688  3021739 /usr/lib/locale/locale-archive
xeyes   10144 steeldriver  mem    REG              252,0    22616  3022756 /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
xeyes   10144 steeldriver  mem    REG              252,0    14456  3022745 /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
xeyes   10144 steeldriver  mem    REG              252,0    18936 10354853 /lib/x86_64-linux-gnu/libuuid.so.1.3.0
xeyes   10144 steeldriver  mem    REG              252,0    14664 10356586 /lib/x86_64-linux-gnu/libdl-2.19.so
xeyes   10144 steeldriver  mem    REG              252,0   125392  3023815 /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
xeyes   10144 steeldriver  mem    REG              252,0    98288  3022616 /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
xeyes   10144 steeldriver  mem    REG              252,0    30896  3022737 /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
xeyes   10144 steeldriver  mem    REG              252,0  1840928 10356602 /lib/x86_64-linux-gnu/libc-2.19.so
xeyes   10144 steeldriver  mem    REG              252,0  1071552 10356583 /lib/x86_64-linux-gnu/libm-2.19.so
xeyes   10144 steeldriver  mem    REG              252,0    39352  3026395 /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
xeyes   10144 steeldriver  mem    REG              252,0  1265072  3022741 /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
xeyes   10144 steeldriver  mem    REG              252,0   413232  3022784 /usr/lib/x86_64-linux-gnu/libXt.so.6.0.0
xeyes   10144 steeldriver  mem    REG              252,0   103016  3022770 /usr/lib/x86_64-linux-gnu/libXmu.so.6.2.0
xeyes   10144 steeldriver  mem    REG              252,0    73288  3026322 /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
xeyes   10144 steeldriver  mem    REG              252,0   149120 10356595 /lib/x86_64-linux-gnu/ld-2.19.so
xeyes   10144 steeldriver    0u   CHR              136,4      0t0        7 /dev/pts/4
xeyes   10144 steeldriver    1u   CHR              136,4      0t0        7 /dev/pts/4
xeyes   10144 steeldriver    2w   CHR                1,3      0t0     1050 /dev/null
xeyes   10144 steeldriver    3u  unix 0x0000000000000000      0t0   135503 socket
xeyes   10144 steeldriver    4r   REG              252,0    40510  3410593 /usr/share/X11/locale/locale.dir

```

Beyond that, there's 'strace' of course

---

### Post by raja.genupula on 2016-07-22
Ok Let me avoid pasting complex command :P

1. lsof | grep <PID>

2. strace and ptrace will also help you if you are trying to monitor that process activity.

---

