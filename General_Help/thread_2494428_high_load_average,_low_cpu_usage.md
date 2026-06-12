---
title: "high load average, low cpu usage"
date: 2024-01-16
forum: General Help
---

### Post by tokar93 on 2024-01-16
Hi

My Ubuntu 22.04.03 seems to be on a high load average whit barely any CPU activity. So i am trying to troubleshoot the problem and top dont seems to be giving me any clue on what can be running that make the load act like this.

top - 16:27:43 up  5:27,  1 user,  load average: 7.00, 7.00, 7.00
Tasks: 131 total,   1 running, 130 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  0.0 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3858.9 total,   2246.5 free,    443.8 used,   1168.5 buff/cache
MiB Swap:   3859.0 total,   3859.0 free,      0.0 used.   3175.3 avail Mem

Any suggestions?

---

### Post by TheFu on 2024-01-16
Check the system logs.

CPU = Load, so the statement doesn't make sense.  

Your box is 99% idle.
Now, if you are looking at the three "load numbers", those are averages over the last 1, 5, and 15 minutes, so if a job just completed, it will take some time for them to average back down. The manpage for **top** will have more details.  Generally, load numbers will be tied to the number of cores engaged.

Here's the output from one of my systems:
```
top - 16:17:36 up 30 days,  8:29,  1 user,  load average: 0.04, 0.07, 0.02
Tasks: 235 total,   2 running, 233 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.3 us,  0.5 sy,  0.0 ni, 96.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.2 st
MiB Mem :   5874.0 total,    385.1 free,   5097.0 used,    391.9 buff/cache
MiB Swap:   1873.0 total,   1867.2 free,      5.8 used.    494.5 avail Mem 

```

BTW, whenever posting terminal output, using code tags really helps so columns+spacing are maintained.

---

### Post by tokar93 on 2024-01-17
Yes i know if it would take some time for the average to go down but the  problem is that it don`t seems to be happen. It still seems to be around  the same as the first post that i made. 

But here is a new one whit the code tag being use. 

```
top - 10:23:24 up 23:22,  1 user,  load average: 7.04, 7.05, 7.01
Tasks: 139 total,   1 running, 138 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.1 sy,  0.0 ni, 99.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3858.9 total,   1588.4 free,    812.5 used,   1458.0 buff/cache
MiB Swap:   3859.0 total,   3859.0 free,      0.0 used.   2822.4 avail Mem
```

Something is running here that is not showing or maybe related to some disk problem?

---

### Post by TheFu on 2024-01-17
Run **xload**. What does it show?
Also the **uptime** command will show the load.

Looks like something in a new kernel that top uses, but perhaps the others don't use ... my 22.04 box is still on 5.15.x kernels. If you are running a 6.x.x kernel, it could be a change in the reporting broke some old things.

---

### Post by tokar93 on 2024-01-17
> **TheFu said:**
> Run **xload**. What does it show?
Also the **uptime** command will show the load.

Looks like something in a new kernel that top uses, but perhaps the others don't use ... my 22.04 box is still on 5.15.x kernels. If you are running a 6.x.x kernel, it could be a change in the reporting broke some old things.

I dont have **xload **install and it seems like you need a display for that when you install and run it? 

```
tokar86a@plex:~$ xload
Error: Can't open display:
```

Uptime is showing the same information. 

```
tokar86a@plex:~$ uptime
 16:12:50 up 57 min,  1 user,  load average: 7.06, 7.06, 6.92
```

22.04.3 LTS (GNU/Linux 6.5.0-14-generic x86_64) yes i am running the new kernel and the other machine that i have use the same kernel and they have not the same problem. It is something that have happen in my plex server machine.

---

### Post by TheFu on 2024-01-17
> **tokar93 said:**
> I dont have **xload **install and it seems like you need a display for that when you install and run it? 

```
tokar86a@plex:~$ xload
Error: Can't open display:
```

Uptime is showing the same information. 

```
tokar86a@plex:~$ uptime
 16:12:50 up 57 min,  1 user,  load average: 7.06, 7.06, 6.92
```

22.04.3 LTS (GNU/Linux 6.5.0-14-generic x86_64) yes i am running the new kernel and the other machine that i have use the same kernel and they have not the same problem. It is something that have happen in my plex server machine.

Can you run a 5.xx kernel?

Do you know how to run remote X11 programs over ssh?  It is a basic skill.  Of course, the machine you sit behind will need an X/Server.

---

### Post by tokar93 on 2024-01-17
No i don`t think i can remote in X11 programs over ssh. Nothing that i have done before and all the monitoring software that i have try showing the same numbers.

---

### Post by MAFoElffen on 2024-01-17
I would probably use this to look at the process state flags, filtering out all that are idle, sending it to a log to review
```

ps -e v | awk '$9 !~ /0\.0/' > temp-processes.log

```
Then look at the states from that output, and use this key from man page 'ps' to interpret the states
```

state    The state is given by a sequence of characters, for example, "RWNA". The      first character indicates the run state of the process:
D    Marks a process in disk (or other short term, uninterruptible) wait.
I    Marks a process that is idle (sleeping for longer than about 20 seconds).  
L    Marks a process that is waiting to acquire a lock.
R    Marks a runnable process.
S    Marks a process that is sleeping for less than about 20 seconds.
T    Marks a stopped process.
W    Marks an idle interrupt thread.
Z    Marks a dead process (a "zombie").

```
"D" and "R" in the 3rd Column (STAT) are the ones that usually be the culprits.

That is where I would start...

---

### Post by TheFu on 2024-01-17
> **tokar93 said:**
> No i don`t think i can remote in X11 programs over ssh. Nothing that i have done before.

[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) explains how.

But if your workstation has an X/Server, then you can run this command at the server to run almost any program remotely.

```
ssh -X userid@IP-address xload
```
Give it 2 seconds for the little **xload** window to display locally on your system.

My web browser is running this way, for example. 
Same for my email program and a number of other tools.  

It is how I work and how all old-timer UNIX people work and have since the 1980s. The system where something is displayed has very little to do with there it runs.  There's no way to tell if a program is running locally or remote under X11 used this way. The integration into a desktop is complete.

---

### Post by tokar93 on 2024-01-17
> **MAFoElffen said:**
> I would probably use this to look at the process state flags, filtering out all that are idle, sending it to a log to review
```

ps -e v | awk '$9 !~ /0\.0/' > temp-processes.log

```
Then look at the states from that output, and use this key from man page 'ps' to interpret the states
```

state    The state is given by a sequence of characters, for example, "RWNA". The      first character indicates the run state of the process:
D    Marks a process in disk (or other short term, uninterruptible) wait.
I    Marks a process that is idle (sleeping for longer than about 20 seconds).  
L    Marks a process that is waiting to acquire a lock.
R    Marks a runnable process.
S    Marks a process that is sleeping for less than about 20 seconds.
T    Marks a stopped process.
W    Marks an idle interrupt thread.
Z    Marks a dead process (a "zombie").

```
"D" and "R" in the 3rd Column (STAT) are the ones that usually be the culprits.

That is where I would start...

This is what i get in the temp file.

```
    PID TTY      STAT   TIME  MAJFL   TRS   DRS   RSS %MEM COMMAND
      1 ?        Ss     0:03    168     0 167552 12876  0.3 /sbin/init
    310 ?        S<s    0:00    196     0 56272 22020  0.5 /lib/systemd/systemd-journald
    351 ?        SLsl   0:00     20     0 289480 27520  0.6 /sbin/multipathd -d -s
    354 ?        Ss     0:00      3     0 25764  6144  0.1 /lib/systemd/systemd-udevd
    531 ?        Ssl    0:00      3     0 89360  7424  0.1 /lib/systemd/systemd-timesyncd
    629 ?        Ss     0:00     20     0 16124  8448  0.2 /lib/systemd/systemd-networkd
    631 ?        Ss     0:00     54     0 25668 13408  0.3 /lib/systemd/systemd-resolved
    662 ?        Ss     0:04     12     0  8736  5248  0.1 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
    667 ?        Ss     0:00     20     0 29072 19072  0.4 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers
    671 ?        Ssl    0:13    149     0 1161636 22224  0.5 /usr/bin/prometheus-node-exporter
    674 ?        Ssl    0:01    312     0 1393516 30888  0.7 /usr/lib/snapd/snapd
    682 ?        Ssl    0:00    357     0 596632 27736  0.7 /usr/sbin/syslog-ng -F
    687 ?        Ss     0:00      6     0 15528  7680  0.1 /lib/systemd/systemd-logind
    714 ?        Ssl    0:34    697     0 230304 104844  2.6 /usr/lib/plexmediaserver/Plex Media Server
    756 ?        Ss     0:00      0     0 15432  9216  0.2 sshd: /usr/sbin/sshd -D 
[listener] 0 of 10-100 startups
    774 ?        Ssl    0:00     12     0 107220 21632  0.5 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
   1148 ?        SNl    0:05     73     0 64880 43728  1.1 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-fb6452ebf/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 1.32.8.7639-fb6452ebf /usr/lib/plexmediaserver/Resources/Plug-ins-fb6452ebf/System.bundle
   1199 ?        Ss     0:00      2     0 41340 31320  0.7 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
   1229 ?        Sl     0:01     43     0 43496 16052  0.4 /usr/lib/plexmediaserver/Plex DLNA Server
   1230 ?        Sl     0:03     58     0 43936 13312  0.3 /usr/lib/plexmediaserver/Plex Tuner Service /usr/lib/plexmediaserver/Resources/Tuner/Private /usr/lib/plexmediaserver/Resources/Tuner/Shared 1.32.8.7639-fb6452ebf 32600
   1308 ?        Ssl    0:02     13     0 1947432 61252  1.5 /usr/bin/crowdsec -c /etc/crowdsec/config.yaml
   1349 ?        S      0:00     16     0 162184 7808  0.1 journalctl --follow -n 0 _SYSTEMD_UNIT=smb.service
   1350 ?        S      0:00     43     0 252296 10496  0.2 journalctl --follow -n 0 _SYSTEMD_UNIT=ssh.service
   4104 ?        Ssl    0:00     78     0 292992 20096  0.5 /usr/libexec/packagekitd
   4108 ?        Ssl    0:00      4     0 234500 7424  0.1 /usr/libexec/polkitd --no-debug
   5641 ?        Sl     0:14      0     0 49256 19220  0.4 /usr/lib/plexmediaserver/Plex Transcoder -codec:0 h264 -codec:1 eac3_eae -eae_prefix:1 x1k1l2lq07t9easyo8es90n3_ -noaccurate_seek -analyzeduration 20000000 -probesize 20000000 -i  -map 0:0 -codec:0 copy -filter_complex [0:1] aresample=async=1:ochl='stereo':rematrix_maxval=0.000000dB:osr=48000[0] -map [0] -metadata:s:1 language=eng -codec:1 aac -b:1 256k -f dash -seg_duration 5 -dash_segment_type mp4 -init_seg_name init-stream$RepresentationID$.m4s -media_seg_name chunk-stream$RepresentationID$-$Number%05d$.m4s -window_size 5 -delete_removed false -skip_to_segment 1 -time_delta 0.0625 -manifest_name http://127.0.0.1:32400/video/:/transcode/session/x1k1l2lq07t9easyo8es90n3/049a67d6-1aef-40dd-9d84-3b0c17855dbf/manifest?X-Plex-Http-Pipeline=infinite -avoid_negative_ts disabled -map_metadata -1 -map_chapters -1 dash -map 0:2 -metadata:s:0 language=eng -codec:0 ass -strict_ts:0 0 -f segment -segment_format ass -segment_time 1 -segment_header_filename sub-header -segment_start_number 0 -segment_list http://127.0.0.1:32400/video/:/transcode/session/x1k1l2lq07t9easyo8es90n3/049a67d6-1aef-40dd-9d84-3b0c17855dbf/manifest?stream=subtitles&X-Plex-Http-Pipeline=infinite -segment_list_type csv -segment_list_size 5 -segment_list_separate_stream_times 1 -segment_format_options ignore_readorder=1 -segment_list_unfinished 1 -fflags +flush_packets sub-chunk-%05d -start_at_zero -copyts -vsync cfr -y -nostats -loglevel quiet -loglevel_plex error -progressurl http://127.0.0.1:32400/video/:/transcode/session/x1k1l2lq07t9easyo8es90n3/049a67d6-1aef-40dd-9d84-3b0c17855dbf/progress
   5755 ?        Ss     0:00      0     0 17184 10880  0.2 sshd: tokar86a [priv]
   5758 ?        Ss     0:00      0   893 16290  9728  0.2 /lib/systemd/systemd --user
   5759 ?        S      0:00      0     0 170464 6720  0.1 (sd-pam)
   5785 ?        S      0:00      0     0 17316  7932  0.2 sshd: tokar86a@pts/0
   5786 pts/0    Ss     0:00      0   891  4284  4096  0.1 -bash
```

---

### Post by MAFoElffen on 2024-01-17
It could be intermittent. Because there is nothing there "at that moment" that is causing a load like that. But that was a filter on all processes that were taking memory above 0%...

Try this, which is filtered on CPU% above 0% in column 4
```

ps -e -f | awk '$4 !~ /0/' > tmp-cpu-proc.log

```

---

### Post by tokar93 on 2024-01-17
> **MAFoElffen said:**
> It could be intermittent. Because there is nothing there "at that moment" that is causing a load like that. But that was a filter on all processes that were taking memory above 0%...

Try this, which is filtered on CPU% above 0% in column 3
```

ps -e -f | awk '$4 !~ /0/' > tmp-cpu-proc.log

```

```
    PID TTY      STAT   TIME  MAJFL   TRS   DRS   RSS %MEM COMMAND


```

Seems like i get nothing here.

---

### Post by MAFoElffen on 2024-01-17
My server and workstation are sitting idle right now, and show the same if idle...

Here is my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ps -e -f | awk '$4 !~ /0/'
UID          PID    PPID  C STIME TTY          TIME CMD
root        3813    3501  2 Jan14 tty7     01:31:38 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
mafoelf+  105931    5663  4 Jan14 ?        02:34:42 /usr/bin/python3 /usr/bin/virt-manager
mafoelf+  344218    6014  4 Jan15 ?        01:59:16 /snap/firefox/3626/usr/lib/firefox/firefox
mafoelf+ 1533725  344218 11 08:09 ?        00:02:00 /snap/firefox/3626/usr/lib/firefox/firefox -contentproc -childID 1952 -isForBrowser -prefsLen 32270 -prefMapSize 240249 -jsInitLen 229864 -parentBuildID 20240108223316 -greomni /snap/firefox/3626/usr/lib/firefox/omni.ja -appomni /snap/firefox/3626/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/3626/usr/lib/firefox/browser {1ca31eb7-3163-4f83-af5e-f8a1ed978518} 344218 true tab
mafoelf+ 1534426  344218  2 08:10 ?        00:00:25 /snap/firefox/3626/usr/lib/firefox/firefox -contentproc -childID 1953 -isForBrowser -prefsLen 32270 -prefMapSize 240249 -jsInitLen 229864 -parentBuildID 20240108223316 -greomni /snap/firefox/3626/usr/lib/firefox/omni.ja -appomni /snap/firefox/3626/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/3626/usr/lib/firefox/browser {f5a9ce3e-52fd-4d31-bce0-2483a62cf3a2} 344218 true tab
mafoelf+ 1535253  344218  1 08:10 ?        00:00:18 /snap/firefox/3626/usr/lib/firefox/firefox -contentproc -childID 1967 -isForBrowser -prefsLen 32270 -prefMapSize 240249 -jsInitLen 229864 -parentBuildID 20240108223316 -greomni /snap/firefox/3626/usr/lib/firefox/omni.ja -appomni /snap/firefox/3626/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/3626/usr/lib/firefox/browser {76c9357c-8d94-40b3-a14a-108a81437162} 344218 true tab
mafoelf+ 1551050  344218  7 08:26 ?        00:00:00 /snap/firefox/3626/usr/lib/firefox/firefox -contentproc -childID 2021 -isForBrowser -prefsLen 32270 -prefMapSize 240249 -jsInitLen 229864 -parentBuildID 20240108223316 -greomni /snap/firefox/3626/usr/lib/firefox/omni.ja -appomni /snap/firefox/3626/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/3626/usr/lib/firefox/browser {36abeeda-d8ad-4f12-b4be-1ffdce810cf8} 344218 true tab

mafoelffen@Mikes-ThinkPad-T520:~$ grep . /proc/loadavg
0.60 0.58 0.55 1/2717 1554334

```
That sysfs file at the end, those first 3 columns, are where 'top' gets the load avarage for 1, 5, & 15 minutes...

I don't see anything on yours showing where a load like 7% is coming from... At least in that point of time. 

But load is not CPU%... Linux load average is a metric that shows 'the number of tasks' currently executed by the CPU and tasks waiting in the queue. Unlike CPU usage, which measures system performance at a specific point in time, the load average shows performance over a particular period.

So CPU% and MEM% are at a point of time (Now). Load is over a period of time.

---

### Post by tokar93 on 2024-01-17
This sure is strange then. Maybe a strange bug or something then? that`s the only thing i can think of for the moment.

---

### Post by MAFoElffen on 2024-01-17
Or you set those queries up to run/loop over a 5 minute period of time, appending to your temp log files, instead of overwriting them...

That would be a closer picture of what is happening over a 5 minute window.

---

### Post by MAFoElffen on 2024-01-17
So something like this:
```

#!/bin/bash
## Mike Ferreira,<mafoelffen@ubuntu.com>,2023.01.17
#
#  Audit processes to help find load

COUNTER=0

rm ./temp-*-processes.log

while [ $COUNTER -lt 15 ]
do
    echo -e "Check STAT $COUNTER" >> temp-stat-processes.log
    ps -e v | awk '$9 !~ /0\.0/' >> temp-stat-processes.log
    echo -e "Check CPU $COUNTER" >> temp-cpu-processes.log
    ps -e -f | awk '$4 !~ /0/' >> temp-cpu-processes.log
    let COUNTER=COUNTER+1 
    sleep 20
done

```

---

### Post by tokar93 on 2024-01-17
Newer mind it is running now.

---

### Post by MAFoElffen on 2024-01-17
So something "was" running (causing a high load), and ended, and now all is well?

---

### Post by tokar93 on 2024-01-17
> **MAFoElffen said:**
> So something "was" running (causing a high load), and ended, and now all is well?


No more like whit the bash to run.

temp-stat-processes.log file: [https://easyupload.io/5t1f6h](https://easyupload.io/5t1f6h)

You can also find it here: [https://codeshare.io/zyDQNr](https://codeshare.io/zyDQNr)

temp-cpu-processes.log
```
Check CPU 0
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 1
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 2
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 3
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 4
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 5
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 6
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 7
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 8
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 9
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 10
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 11
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 12
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 13
UID          PID    PPID  C STIME TTY          TIME CMD
Check CPU 14
UID          PID    PPID  C STIME TTY          TIME CMD

```

---

### Post by tokar93 on 2024-01-17
So something is really acting up here as i cannot see anything wrong here from my point of view but something is still making the load average go up from boot and stay steady around 7.

---

### Post by TheFu on 2024-01-17
I think something changed how the kernel reports load and none of the popular programs are properly displaying it.  This is probably hardware specific - for example, AMD and Intel do things different as so different models of each CPU.

We aren't going to solve it here. If **top** is actively developed, open a bug with that team, or open a bug in landscape using the built-in bug reporting tool on Ubuntu - I assume it still exists.

---

### Post by Doug S on 2024-01-17
The load average information is sampled. It is possible to have alias effects resulting in misleading information.

Example: a 50% load on one CPU (5) showing as 0 load. It has been running for a few minutes:

```

top - 22:16:26 up 1 day,  4:31,  3 users,  load average: 0.07, 0.06, 0.02
Tasks: 213 total,   2 running, 211 sleeping,   0 stopped,   0 zombie
%Cpu0  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu2  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu4  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu5  :  0.0 us,  0.0 sy,  0.0 ni,[COLOR="#FF0000"]100.0 id[/COLOR],  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu6  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu7  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu8  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu9  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu10 :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu11 :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  31927.2 total,  30742.7 free,    814.8 used,    784.2 buff/cache
MiB Swap:   8192.0 total,   8192.0 free,      0.0 used.  31112.4 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   3864 doug      20   0    2656   1536   1536 R  [COLOR="#FF0000"]50.0 [/COLOR]  0.0   0:05.45 consume
   3859 doug      20   0   11948   5760   3584 R   0.3   0.0   0:00.17 top

```

It used to be easy also show the converse, i.e. a load of 1 for an actual low load, but that was in 2012. It seems to be more difficult now. If there is a bug it would be in the kernel code.

How did I do the above example? I ran the work/sleep frequency at the exact same rate as the kernel tick, and so while the CPU was actually doing a lot, it was always idle when the load average code was executed.

The last change to the load average code was in kernel 5.18:

```

doug@s19:~/kernel/linux$ git log --oneline kernel/sched/loadavg.c
801c14195510 sched/headers: Introduce kernel/sched/build_utility.c and build multiple .c files there
e6fe3f422be1 sched: Make multiple runqueue task counters 32-bit
3b03706fa621 sched: Fix various typos
...

doug@s19:~/kernel/linux$ git tag --contains 801c14195510
v5.18
v5.18-rc1
...
v6.7

```

---

### Post by MAFoElffen on 2024-01-17
I don't see any processes doing much, except maybe Plex @ 3.3% memory. Even then, the CPU% has stayed at 0% over 5 minutes.

Am I confused with that?

---

### Post by tokar93 on 2024-01-18
i decided to reinstall the device as something sure seems to be wrong here.

---

### Post by Doug S on 2024-01-18
> **MAFoElffen said:**
> I don't see any processes doing much, except maybe Plex @ 3.3% memory. Even then, the CPU% has stayed at 0% over 5 minutes.

Am I confused with that?My example was not a good one. I was just trying to say/show that because the load average is a sampled calculation it can give incorrect information.

I'd be interested to know if the re-install solved the OP's issue.

---

### Post by MAFoElffen on 2024-01-18
I decided to keep track of my Workstation from time to time to check loads... If high, I would audit my Workstation with this script:
```

#!/usr/bin/bash
#
## Mike Ferreira,<mafoelffen@ubuntu.com>,2023.01.17
#
#  Audit processes to help find load
COUNTER=0
rm ./audit-processes.log
while [ $COUNTER -lt 15 ]
do
    echo -e "Check STAT $COUNTER" >> audit-processes.log
    ps -e v | awk '$9 !~ /0\.0/' >> audit-processes.log
    echo "" >> audit-processes.log
    echo -e "Check CPU $COUNTER" >> audit-processes.log
    ps -e -f | awk '$4 !~ /0/' >> audit-processes.log
    echo "" >> audit-processes.log
    echo -e "Check loadavg" >> audit-processes.log
    grep . /proc/loadavg >> audit-processes.log
    echo "" >> audit-processes.log
    echo -e "Check stat" >> audit-processes.log
    grep . /proc/stat >> audit-processes.log
    let COUNTER=COUNTER+1 
    sleep 20
done

```
My load this morning was over 6 at idle. I ran it. The sampling was 15 times, every 20 seconds = 5 minutes. 

The audit log is uploaded to: [https://paste.ubuntu.com/p/7Fj877KzK6/](https://paste.ubuntu.com/p/7Fj877KzK6/)

I included looking at the /proc/stat file. The key to the columns of that is:
```

1     user     Time spent with normal processing in user mode.
2     nice     Time spent with niced processes in user mode.
3     system     Time spent running in kernel mode.
4     idle     Time spent in vacations twiddling thumbs.
5     iowait     Time spent waiting for I/O to completed. This is considered idle time too.     since 2.5.41
6     irq     Time spent serving hardware interrupts. See the description of the intr line for more details.     since 2.6.0
7     softirq     Time spent serving software interrupts.     since 2.6.0
8     steal     Time stolen by other operating systems running in a virtual environment.     since 2.6.11
9     guest     Time spent for running a virtual CPU or guest OS under the control of the kernel.     since 2.6.24

```
My workstation has Plex, but no-one is watching. The only things running are my Conky Desktop samplings, and it has an update pending dialog on the Desktop... And a system error dialog, which when I selected "show me", showed no errors...

Now I'm going to cancel that dialog, and apply my updates manually in terminal then reboot, wait 15 minutes, then run again...

---

### Post by MAFoElffen on 2024-01-18
My load at ssh login says 6... Ran audit:[https://paste.ubuntu.com/p/n9xtr849jW/](https://paste.ubuntu.com/p/n9xtr849jW/)

---

### Post by Doug S on 2024-01-18
Hi Mike,

Extremely interesting. Thanks.
From your first data, I processed a little, for my own understanding. I hope this formats properly:

```
user	nice	system	idle	iowait	irq	softirq	total	HZ
								
82	0	108	63857	9	0	0	64056	100.1
84	0	100	63862	8	0	0	64054	100.1
88	0	107	63863	8	0	1	64067	100.1
78	1	115	63861	7	0	0	64062	100.1
82	1	128	63860	10	0	1	64082	100.1
78	0	118	63859	9	0	0	64064	100.1
88	1	112	63862	8	0	1	64072	100.1
84	0	106	63862	8	0	0	64060	100.1
79	1	107	63867	8	0	0	64062	100.1
81	0	113	63864	8	0	0	64066	100.1
93	0	104	63838	23	0	1	64059	100.1
82	1	109	63862	8	0	1	64063	100.1
91	0	110	63859	8	0	2	64070	100.1
90	0	119	63861	11	0	2	64083	100.1
```

It is not clear to me why the kernel tick is reverse calculating to be 100Hz instead of 250Hz (or 1000Hz, if you are using a low latency kernel).

EDIT 1: It seems /proc/stat is not Jiffy based, but USER_HZ based. Years and years ago they used to be the same, 100Hz. Now they are not the same.

EDIT 2: There does seems to be a lot of soft interrupts going on:

```

Softirqs (number of calls)											
Total	sirq1	sirq2	sirq3	sirq4	sirq5	sirq6	sirq7	sirq8	sirq9	sirq10	persec
21872	0	1895	123	2825	10	0	20	7518	0	9481	1093.6
21577	0	1852	120	2530	10	0	21	7725	0	9319	1078.9
20328	0	1801	113	2547	10	0	20	7201	0	8636	1016.4
20569	0	1870	124	2644	10	0	21	7702	0	8198	1028.5
20353	0	1864	117	2470	10	0	20	7868	0	8004	1017.7
21234	0	1919	117	2687	10	0	19	7911	0	8571	1061.7
21462	0	1867	126	2724	10	0	21	7954	0	8760	1073.1
20962	0	1834	120	2441	10	0	20	8190	0	8347	1048.1
20990	0	1845	118	2531	10	0	21	8061	0	8404	1049.5
20897	0	1841	122	2511	10	0	20	8165	0	8228	1044.9
22845	0	1870	124	2779	35	0	21	8533	0	9483	1142.3
22603	0	1801	113	2497	10	0	20	7995	0	10167	1130.2
22171	0	1852	123	2636	10	0	21	8394	0	9135	1108.6
22760	0	1829	124	2545	9	0	21	8501	0	9731	1138.0


```

---

### Post by tokar93 on 2024-01-18
> **Doug S said:**
> My example was not a good one. I was just trying to say/show that because the load average is a sampled calculation it can give incorrect information.

I'd be interested to know if the re-install solved the OP's issue.

Yes the reinstall fix the problem if you wear talking about me.

---

### Post by MAFoElffen on 2024-01-19
@Doug S ---
TurboStat sampling: [https://paste.ubuntu.com/p/kWMht8TxPK/](https://paste.ubuntu.com/p/kWMht8TxPK/)
Interrupts sampling: [https://paste.ubuntu.com/p/hB5HBmwC73/](https://paste.ubuntu.com/p/hB5HBmwC73/)

Then I decided to give it a load for comparison:
```

mafoelffen@msi-ubuntu:~$ virsh list
 Id   Name                           State
----------------------------------------------
 1    lunar_lander-01                running
 5    opensolaris2009.06             running
 6    opensusetumbleweed             running
 7    fedora                         running
 8    popos22.04-3                   running
 9    rhel8                          running
 10   ubuntu22.04-btrfs01            running
 11   ubuntu22.04-ZFS-ZRAID-EFI-01   running
 14   ubuntu22.04-lvm01              running
 15   ubuntu-arm64                   running
 16   ubuntu22.04-3                  running
 17   vista-vm01                     running
 18   win10-01                       running
 19   ovirt-node-01                  running
 20   ubuntu server test             running

```
TurboStat Sampling: [https://paste.ubuntu.com/p/S4fwZKhhn6/](https://paste.ubuntu.com/p/S4fwZKhhn6/)
Audit-load: [https://paste.ubuntu.com/p/vv8H4PsB9G/](https://paste.ubuntu.com/p/vv8H4PsB9G/)
These two samplings were running at the same time, the first, then the second, started about a minute later or so.

Note: None of that drags down the system... That's it's job. Just goes along doing it's jobs fine.

Even with this on /proc/loadavg:
```

138.41 118.86 67.49 3/2516 380691

```

---

### Post by Doug S on 2024-01-19
> **MAFoElffen said:**
> 
Even with this on /proc/loadavg:
```

138.41 118.86 67.49 3/2516 380691

```Hi Mike,

There is too much going on with the data samples you supplied. Would it be possible to get the turbostat data when you have the load average of 6 conditions that you had yesterday?

I also wonder if [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049242") is relevant? (also mentioned in a PM earlier, but listed here for other readers.)

---

### Post by MAFoElffen on 2024-01-19
The first two samplings where at between 6-7 last night. The second two were with things loads up to cause a higher load.

Is running at about 6.2 load now. Shutting down 2 VM's that I was testing on, and will wait about 15 minutes so that the stats settle. I'll kick off all 3 samplings at once. Then upload them to pastebins... BRB

PM'ed you back on some things.

---

### Post by MAFoElffen on 2024-01-19
The 3 samplings:
[https://paste.ubuntu.com/p/jrgThcZXXS/](https://paste.ubuntu.com/p/jrgThcZXXS/)
[https://paste.ubuntu.com/p/j9v42nYZ6F/](https://paste.ubuntu.com/p/j9v42nYZ6F/)
[https://paste.ubuntu.com/p/f4R4SvQdH8/](https://paste.ubuntu.com/p/f4R4SvQdH8/)

---

### Post by Doug S on 2024-01-19
Have a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2048945") and the related [upstream bug]("https://bugzilla.kernel.org/show_bug.cgi?id=217914"), particularly [comment #8]("https://bugzilla.kernel.org/show_bug.cgi?id=217914#c8"). And my suggestion is to try [mainline kernel 6.7]("https://kernel.ubuntu.com/mainline/v6.7/"), just as a test.

It'll take me awhile to go through the data you provided.

---

### Post by MAFoElffen on 2024-01-19
> **Doug S said:**
> Have a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2048945") and the related [upstream bug]("https://bugzilla.kernel.org/show_bug.cgi?id=217914"), particularly [comment #8]("https://bugzilla.kernel.org/show_bug.cgi?id=217914#c8"). And my suggestion is to try [mainline kernel 6.7]("https://kernel.ubuntu.com/mainline/v6.7/"), just as a test.

Compromise:
VM Desktop 22.04.3, pass through 8 vcpu's, 16GB RAM...

You want me to set it to SCSI or SATA as disk? That Bug says SCSI, but I am getting this with SATA & NVMe... So I'm thinking SATA with kernels 5.15, 6.2, 6.5 & 6.7.

EDIT: Ready with these:
```

mafoelffen@ktest-00:~/Downloads/Kernels$ apt list linux-image-*-generic --installed
Listing... Done
linux-image-5.15.0-94-generic/jammy-proposed,now 5.15.0-94.104 amd64 [installed,automatic]
linux-image-6.2.0-26-generic/jammy-updates,jammy-security,now 6.2.0-26.26~22.04.1 amd64 [installed,auto-removable]
linux-image-6.2.0-39-generic/jammy-updates,jammy-security,now 6.2.0-39.40~22.04.1 amd64 [installed]
linux-image-6.5.0-14-generic/jammy-updates,jammy-security,now 6.5.0-14.14~22.04.1 amd64 [installed,automatic]
linux-image-unsigned-6.7.0-060700-generic/now 6.7.0-060700.202401072033 amd64 [installed,local]

```

---

### Post by Doug S on 2024-01-19
> **MAFoElffen said:**
> You want me to set it to SCSI or SATA as disk? That Bug says SCSI, but I am getting this with SATA & NVMe yes, sorry.  I have since been looking your /proc/interrupts postings and didn't see any SCSI.


> **MAFoElffen said:**
> Ready with these:
```

mafoelffen@ktest-00:~/Downloads/Kernels$ apt list linux-image-*-generic --installed
Listing... Done
linux-image-5.15.0-94-generic/jammy-proposed,now 5.15.0-94.104 amd64 [installed,automatic]
linux-image-6.2.0-26-generic/jammy-updates,jammy-security,now 6.2.0-26.26~22.04.1 amd64 [installed,auto-removable]
linux-image-6.2.0-39-generic/jammy-updates,jammy-security,now 6.2.0-39.40~22.04.1 amd64 [installed]
linux-image-6.5.0-14-generic/jammy-updates,jammy-security,now 6.5.0-14.14~22.04.1 amd64 [installed,automatic]
linux-image-unsigned-6.7.0-060700-generic/now 6.7.0-060700.202401072033 amd64 [installed,local]

```Try the 6.7 kernel. It would be my input to always try the latest mainline kernel with these kind of issues. Then we know if it is fixed upstream and we merely have to wait for it to be back-ported or if more investigation is needed.

---

### Post by MAFoElffen on 2024-01-19
5.15.0-94-generic:
[https://pastebin.ubuntu.com/p/fVYhCyghMQ/](https://pastebin.ubuntu.com/p/fVYhCyghMQ/)
[https://pastebin.ubuntu.com/p/G7gzK7GGMW/](https://pastebin.ubuntu.com/p/G7gzK7GGMW/)

6.2.0-39-generic:
[https://pastebin.ubuntu.com/p/NqQy6G9w86/](https://pastebin.ubuntu.com/p/NqQy6G9w86/)
[https://pastebin.ubuntu.com/p/5MCXkKd9pc/](https://pastebin.ubuntu.com/p/5MCXkKd9pc/)

6.5.0-14-generic:
[https://pastebin.ubuntu.com/p/vQ23DmtPy9/](https://pastebin.ubuntu.com/p/vQ23DmtPy9/)
[https://pastebin.ubuntu.com/p/qwvW4V4Y6K/](https://pastebin.ubuntu.com/p/qwvW4V4Y6K/)

I have to reinstall. That VM was installed as ZFS-On-Root, and doesn't want to boot as 22.04 w/ mainline kernel 6.7.0. Have to get back to you with that much later tonight. (errands to do)

---

### Post by Doug S on 2024-01-19
Mainly interested in reported load averages in that data:

```

5.15.0-94-generic:
0.05 0.07 0.03 1/692 5777
0.03 0.07 0.03 1/685 5991
0.02 0.06 0.03 1/686 6065
0.02 0.06 0.02 1/672 6230
0.01 0.05 0.02 1/669 6271
0.01 0.05 0.02 1/671 6313
0.00 0.05 0.02 1/671 6375
0.00 0.04 0.02 1/667 6410
0.00 0.04 0.02 1/668 6443
0.00 0.03 0.01 1/669 6482
0.00 0.03 0.01 1/669 6515
0.00 0.03 0.01 1/670 6549
0.00 0.03 0.01 1/672 6589
0.00 0.02 0.01 1/675 6624
0.00 0.02 0.00 1/673 6713

6.2.0-39-generic:
0.15 0.13 0.06 1/695 5310
0.10 0.12 0.05 1/696 5426
0.15 0.13 0.06 1/694 5488
0.10 0.12 0.06 1/696 5560
0.07 0.11 0.05 1/692 5613
0.05 0.10 0.05 1/692 5777
0.04 0.10 0.05 1/690 5837
0.03 0.09 0.05 1/691 5938
0.02 0.08 0.05 1/675 6025
0.01 0.08 0.04 1/673 6141
0.01 0.07 0.04 1/673 6187
0.00 0.06 0.04 1/671 6245
0.00 0.06 0.04 1/674 6305
0.00 0.05 0.04 1/673 6350
0.00 0.05 0.04 1/670 6404

6.5.0-14-generic:
1.24 0.35 0.12 1/714 3007
1.45 0.46 0.16 1/728 3132
1.61 0.56 0.20 1/722 3155
1.72 0.66 0.24 1/721 3175
1.80 0.74 0.28 1/725 3200
1.86 0.83 0.32 1/724 3216
1.90 0.90 0.36 1/724 3239
1.93 0.97 0.39 1/724 3260
1.95 1.04 0.43 1/721 3282
1.96 1.10 0.46 1/724 3301
1.98 1.16 0.49 1/722 3314
1.98 1.22 0.53 1/719 3329
1.99 1.27 0.56 1/720 3344
1.99 1.32 0.59 1/705 3363
2.00 1.36 0.62 1/701 3377

```

---

### Post by MAFoElffen on 2024-01-19
6.7.0-060700-generic:
0.08 0.02 0.01 1/606 3199
0.06 0.01 0.00 1/605 3201
0.04 0.01 0.00 1/604 3205
0.03 0.01 0.00 1/604 3208
0.02 0.01 0.00 1/603 3210
0.01 0.01 0.00 1/603 3212
0.01 0.00 0.00 1/604 3215
0.00 0.00 0.00 1/604 3217
0.00 0.00 0.00 1/604 3219
0.00 0.00 0.00 1/604 3221
0.00 0.00 0.00 1/605 3224
0.00 0.00 0.00 1/604 3226
0.00 0.00 0.00 1/604 3228
0.00 0.00 0.00 1/605 3232
0.00 0.00 0.00 1/605 3235

---

### Post by Doug S on 2024-01-20
It is not clear to me why the kernel 6.5 load averages were not hovering around 6, as with previous experiments.
Do we conclude that the issue is fixed in the upstream kernel? Or are more tests required?

---

### Post by MAFoElffen on 2024-01-20
I think other tests are required. 
```

mafoelffen@msi-ubuntu:~$ uname -r 
6.5.0-14-generic
mafoelffen@msi-ubuntu:~$ grep . /proc/loadavg
[COLOR=#ff0000]6.29 6.18 6.08 1/1658 1055150[/COLOR]

```
That is from the physical Workstation at rest.

Those samples from the  last few posts were all similated in KVM VM guest, with a passed through 8 vCPUs, 16GB RAM, Ubuntu 22.04.3... 

I did that so I wouldn't be installing 6.7 on my host... because I have upstream Intel Graphics Support Tests going on there. Lets what I do have on it right now:
```

6.29 6.18 6.08 1/1658 1055150
mafoelffen@msi-ubuntu:~$ apt list linux-image* --installed
Listing... Done
linux-image-5.15.0-91-generic/jammy-updates,jammy-security,now 5.15.0-91.101 amd64 [installed,automatic]
linux-image-6.2.0-39-generic/jammy-updates,jammy-security,now 6.2.0-39.40~22.04.1 amd64 [installed,automatic]
linux-image-6.5.0-14-generic/jammy-updates,jammy-security,now 6.5.0-14.14~22.04.1 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 6.5.0.14.14~22.04.7 amd64 [installed,automatic]
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.91.88 amd64 [installed,automatic]

```
Yes, let me PM you about a detail on that...

---

### Post by Doug S on 2024-01-29
There is another report of high reported load average when the system load is actually low, over on [ask]("https://askubuntu.com/questions/1501766/very-high-system-load-on-ubuntu-22-04-probably-related-to-mounting-samba-cifs-s").
I have been on another time consuming problem and lost track of this one.

---

### Post by MAFoElffen on 2024-01-30
Yes... That (over on AksUbuntu) seems like the same that is going on. Dang. 

I'm thinking we need to look at a bigger picture of what is causing it. But not sure how to capture that, to see what that might be.

I do not have CIFS/SMB shares connected to mine. But I do have some NTFS mounts within mine... For my media files for Plex Server and my old ISO file storage and VM storage for KVM.

The Media Files, I share between Plex Server: Windows and Linux. That way, whichever boot I am into, my wife can still access the Media Server Services. The ISO storage, I share between KVM and Hyper-V. The VM storage is shared between 3 Ubuntu installs. I should really migrate those files off of NTFS, but isn't high enough on the priorities list yet.

---

