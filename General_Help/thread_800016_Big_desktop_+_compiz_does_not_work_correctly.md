---
title: "Big desktop + compiz does not work correctly"
date: 2008-05-19
forum: General Help
---

### Post by quizzelsnatch on 2008-05-19
I have installed my ATI drivers correctly and compiz works fine, but after getting my dual monitors set up and running compiz, if I click on the background (not application windows or icons, but just the background), xserver crashes and restarts without any error message. How can I find out what error I am getting, and further, how can I fix that?

I know it's not my ATI drivers specifically because I've tested it with just one monitor and it does not crash with compiz enabled, and with compiz disabled and two monitors it also does not crash.

---

### Post by quizzelsnatch on 2008-05-28
Oh, I should tell you I am using gnome, x1800xt, 2 identical 20" dell monitors, and all of my packages are up to date.

---

### Post by Forlong on 2008-05-29
Unfortunately, it is most probably a problem with the fglrx driver. It doesn't handle Compiz on dual-head setups well.

Have a look at your /var/log/Xorg.0.log after the crash.

---

### Post by quizzelsnatch on 2008-06-02
Interesting... Don't know what happened, maybe it was the latest update of compiz, but I tried to recreate the error to get a log of the crash and post it for help, and I cannot do it. Sweet.

---

### Post by quizzelsnatch on 2008-06-02
Spoke too soon... does it all the time after about 10 minutes of it being stable. I have looked at /var/log/Xorg.0.log after the crash and there doesn't appear to be anything that looks like an error.

There are the last few lines of the log:
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

However, earlier it does say: (WW) AIGLX: 3D driver claims to not support visual 0x72 for several different 0x*

---

### Post by quizzelsnatch on 2008-06-03
THE CULPRIT HAS BEEN FOUND!
from /var/log/syslog

Jun  2 21:13:07 olympus kernel: [104136.491017] compiz.real[22933]: segfault at 7f7900002093 rip 40fee0 rsp 7ffffc5b2b90 error 4
Jun  2 21:13:08 olympus gdm[22110]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

What does it mean?

---

### Post by RAOF on 2008-06-03
> **quizzelsnatch said:**
> THE CULPRIT HAS BEEN FOUND!
from /var/log/syslog

Jun  2 21:13:07 olympus kernel: [104136.491017] compiz.real[22933]: segfault at 7f7900002093 rip 40fee0 rsp 7ffffc5b2b90 error 4
Jun  2 21:13:08 olympus gdm[22110]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

What does it mean?

Your X server died, taking Compiz with it.  I'm going to go out on a limb and blame the ATI drivers ;).  Compiz is excellent at exposing driver bugs!

You can probably get a core dump file from X by using **ulimit -c unlimited** to set the maximum coredump filesize from its default of 0kb before starting X (or gdm).  You could load this up in gdb, and examine the backtrace, but it's unlikely to help very much except possibly to confirm that it dies in proprietary fglrx code :(.

---

### Post by quizzelsnatch on 2008-06-03
> **RAOF said:**
> Your X server died, taking Compiz with it.  I'm going to go out on a limb and blame the ATI drivers ;).  Compiz is excellent at exposing driver bugs!

You can probably get a core dump file from X by using **ulimit -c unlimited** to set the maximum coredump filesize from its default of 0kb before starting X (or gdm).  You could load this up in gdb, and examine the backtrace, but it's unlikely to help very much except possibly to confirm that it dies in proprietary fglrx code :(.

What I am hearing is: "this problem will never get fixed." Sadface. Thanks. That ends my search for a fix to the problem on the internet.

---

### Post by RAOF on 2008-06-03
> **quizzelsnatch said:**
> What I am hearing is: "this problem will never get fixed." Sadface. Thanks. That ends my search for a fix to the problem on the internet.

Oh, it may well get fixed.  But probably only in a new fglrx driver.  Feel free to file a bug against the linux-restricted-modules package - apparently we've worked out some scheme to forward these bugs on to AMD, so they may well get fixed.  You could possibly try the Xgl X server (package: xserver-xgl), but I'm not sure how well that handles dual-head.

---

### Post by quizzelsnatch on 2008-06-05
> **RAOF said:**
> Oh, it may well get fixed.  But probably only in a new fglrx driver.  Feel free to file a bug against the linux-restricted-modules package - apparently we've worked out some scheme to forward these bugs on to AMD, so they may well get fixed.  You could possibly try the Xgl X server (package: xserver-xgl), but I'm not sure how well that handles dual-head.

I tried the xgl driver, it also crashed on me. Thanks.

---

### Post by fastpakr on 2009-05-06
Bumping this back up.  I tried to find a Launchpad report but haven't found it yet.  This appears to be virtually the same problem, except that I'm only using a single head system. Running 9.04 32 bit, I get occasional X crashes with messages like these in the logs:
> May  6 14:36:37 SC-UBU-1000 kernel: [80214.425884] [drm] Num pipes: 1
May  6 14:36:37 SC-UBU-1000 gdm[2739]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May  6 14:36:37 SC-UBU-1000 kernel: [80214.466396] compiz.real[3484]: segfault at 10 ip 08055c0c sp bf815020 error 4 in compiz.real[8048000+34000]
May  6 14:36:37 SC-UBU-1000 bonobo-activation-server (cjohnson-19635): could not associate with desktop session: Failed to connect to socket /tmp/dbus-l7s0xxdggX: Connection refused
May  6 14:36:38 SC-UBU-1000 acpid: client 2745[0:0] has disconnected 
May  6 14:36:38 SC-UBU-1000 acpid: client connected from 19703[0:0] 
May  6 14:36:39 SC-UBU-1000 kernel: [80216.032748] [drm] Setting GART location based on new memory map
May  6 14:36:39 SC-UBU-1000 kernel: [80216.033825] [drm] Loading R500 Microcode
May  6 14:36:39 SC-UBU-1000 kernel: [80216.033864] [drm] Num pipes: 1
May  6 14:36:39 SC-UBU-1000 kernel: [80216.033870] [drm] writeback test succeeded in 1 usecs

I haven't determined a pattern in what's causing them.  Never doing anything exciting, just web browsing, editing text documents, etc.  There's a sudden flicker to black, then I'm back at the login screen.  If anybody has troubleshooting ideas, I'd be glad to test them.  Video card is id'd as "ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]".  Hope this helps.

---

