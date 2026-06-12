---
title: "systemd-journal 99% CPU load"
date: 2015-05-03
forum: General Help
---

### Post by dmeyermail on 2015-05-03
Hello,
I just upgraded to Ubuntu 15.04 from 14.10 (on a Lenovo T440s) and I have very high CPU usage. In particular systemd-journal, rsyslogd, and evince-thumbnai have extremely high loads.
Here are the first lines from top:

top - 11:29:31 up 16:54,  4 users,  load average: 3,18, 3,15, 2,38
Tasks: 238 total,   3 running, 235 sleeping,   0 stopped,   0 zombie
%Cpu(s): 14,5 us, 15,0 sy,  0,6 ni, 69,3 id,  0,7 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:  12005056 total, 11850172 used,   154884 free,   144720 buffers
KiB Swap: 12278780 total,     6356 used, 12272424 free.  5034672 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
  254 root      20   0   33264   7468   7016 R 100,0  0,1  18:53.91 systemd-journal
  708 syslog    20   0  255896   3772   2844 S  82,9  0,0  14:02.33 rsyslogd
 4780 dani      20   0 5296204 4,769g  14232 R  70,1 41,7  14:13.99 evince-thumbnai
  913 root      20   0  422204  77332  58380 S  12,7  0,6   0:44.73 Xorg
 4530 dani      20   0 1728856 186524 125792 S   6,4  1,6   0:48.00 chromium-browse
 4567 dani      20   0  998416 276548 197892 S   6,4  2,3   0:39.42 chromium-browse
 5812 dani      20   0 1092392 200372  68008 S   6,4  1,7   1:23.64 chromium-browse
    1 root      20   0  182676   5384   3660 S   0,0  0,0   0:01.90 systemd
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.02 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0,0  0,0   0:03.00 rcu_sched
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh
    9 root      20   0       0      0      0 S   0,0  0,0   0:07.88 rcuos/0
   10 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcuob/0
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.93 migration/0
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 watchdog/0
   13 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 watchdog/1  

Right now there is only chrome, emacs two terminals, nautilus, and okular open. There is also dropbox running.
It seems to be that the the problem appears when I open okular. I ran journalctl and I get 

Mai 03 11:11:03 dani-ThinkPad-T440s gnome-session[1112]: page: Error: /usr/share/texlive/texmf-dist/fonts/tfm/public/cm/cmr10.tfm: File corrupted, or not a TFM fileMai 03 11:11:03 dani-ThinkPad-T440s gnome-session[1112]: page: Warning: font `cmr10' not found, trying metric files instead

I reinstalled fonts-lyx and texlive-latex-base, but the problem still persists. Any help would be very much appreciated, as I get very bad battery time as can be expected. Thanks a lot in advance,

Daniel.

---

### Post by tobias-andersson-gidlund on 2015-05-05
Hi,

I had the same problem and both of the processes stopped being a problem when I disabled thumbnailing for dvi files. I found the answer on the following page: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1386120/comments/4](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1386120/comments/4)

Hope it helps you too!

//Tobias

---

