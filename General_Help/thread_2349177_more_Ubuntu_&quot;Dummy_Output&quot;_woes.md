---
title: "more Ubuntu &quot;Dummy Output&quot; woes"
date: 2017-01-11
forum: General Help
---

### Post by crouchy89 on 2017-01-11
Hi,

I recently got a new Dell Precision laptop. When I booted it up for the first time the sound worked no problem. After updating the system that's when the issue started. I went through 3 pages of Google search and couldn't take a fourth

[B]Step 1: Make sure alsa and pulseaudio up to date
[/B]```

sudo apt-get install pulseaudio alsa-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I tried re-installing as well just to be sure. I also reinstalled libasound2:
```

sudo apt-get install --reinstall libasound2

```

[B]Step 2: force reload
[/B]Tried re-starting alsa
```

sudo alsa force-reload  

```



[B]Step 3: Modify alsa-base.conf
[/B]I ran:
```

sudo gedit /etc/modprobe.d/alsa-base.conf

``` 
and added an additional line at the end:
```

options snd-hda-intel model=dell-s14

```
and also tried
```

options snd-hda-intel model=generic

```

rebooting after each attempt

[B]Step 4: modprobe
[/B]Came across this on one page, but didn't get very far
```

sudo modprobe snd-hda-intel
modprobe: ERROR: could not insert 'snd_hda_intel': Required key not available 

```

[B]Step 5: See if soundcard recognized
[/B]If I run:
```

sudo aplay -l
aplay: device_list:268: no soundcards found...

```
I get one answer, but if I run:
```

echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done

```
I get:
```

Sound cards recognized by the system:
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
Sound cards recognized by ALSA:
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
Sound cards recognized by ALSA, and activated:
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)

```

[B]Some other output info
[/B]```

pulseaudio -vvv
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 4.0
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux x86_64 4.4.0-59-generic #80~14.04.1-Ubuntu SMP Fri Jan 6 18:02:02 UTC 2017
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is aa673caf485274a8e352a97d58753788.
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1001/pulse.
I: [pulseaudio] main.c: Using state directory /home/nick/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

```



Any input is greatly appreciated

---

### Post by dragonfly41 on 2017-01-12
When I had some sound problems in my older Dell Inspiron laptop I followed tips found here ...

[http://askubuntu.com/questions/132440/headphone-jack-not-working](http://askubuntu.com/questions/132440/headphone-jack-not-working)

My alsa-base.conf reads ...
```

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m6-amic
```

---

### Post by crouchy89 on 2017-01-12
I added these lines and tried the 3 possible combinations (listed in this thread) for the model, but still only receiving dummy output

---

### Post by dragonfly41 on 2017-01-12
I can only point to references found by searching around ...

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Perhaps try as model setting ... 

```
options snd-hda-intel model=auto
```

and have you tried running ...

```
pavucontrol
```

[Later edit]

You do realise from reading above Troubleshooting guide that you need to reboot after changes?

> [COLOR=#333333][FONT=Ubuntu]wait 10 seconds, [/FONT][/COLOR]**then reboot**[COLOR=#333333][FONT=Ubuntu] (putting the machine to sleep is not enough -- fully power it off and then back on).[/FONT][/COLOR]

---

### Post by crouchy89 on 2017-01-16
Thank you for your suggestion. As the machine was new, and I had only started transferring my backed up files I performed a fresh install of Ubuntu and it seemed to do the trick

---

