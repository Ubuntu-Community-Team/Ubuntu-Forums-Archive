---
title: "too hot?"
date: 2007-03-21
forum: General Help
---

### Post by scuttle.VB on 2007-03-21
i was playing 3dchess on my laptop when suddenly the system rebooted. i checked the system log later and found that the system had reached 99C and hence rebooted.
here is the log:
Mar 19 15:06:58 vb-laptop kernel: [  898.992033] ACPI: Critical trip point
Mar 19 15:06:58 vb-laptop kernel: [  898.992044] Critical temperature reached (99 C), shutting down.
Mar 19 15:06:58 vb-laptop init: tty1 process (3782) killed by signal 15
Mar 19 15:06:58 vb-laptop init: tty2 process (3783) killed by signal 15
Mar 19 15:06:58 vb-laptop init: tty3 process (3784) killed by signal 15
Mar 19 15:06:58 vb-laptop init: tty4 process (3785) killed by signal 15
Mar 19 15:06:58 vb-laptop init: tty5 process (3786) killed by signal 15
Mar 19 15:06:58 vb-laptop init: tty6 process (3787) killed by signal 15
Mar 19 15:06:58 vb-laptop gconfd (vb-4682): Received signal 15, shutting down cleanly
Mar 19 15:06:58 vb-laptop gconfd (vb-4682): Exiting
Mar 19 15:07:01 vb-laptop hcid[4399]: Got disconnected from the system message bus
Mar 19 15:07:03 vb-laptop exiting on signal 15


it had been hardly 15 minutes had laptop had been on. i dont get it.
is there a problem

---

### Post by hardyn on 2007-03-21
I have an idea...

what processor and what kernel are you running...
if you have a sony or asus PM notebook run the i386 kernel...

has one of the fans stalled?

does linux detect your fans, sensing hardware?

the system log will likely tell you if there is a sensor problem.

---

### Post by scuttle.VB on 2007-03-22
my laptop is a hp-compaq one with amd turion 64 bit processor.so i dont think i can run i386 kernel.
also i have noticed that playing games like 3dchess,anagramarama,billiards etc keeps the CPU usage at >=50%. i think this is too high for such games.
i dont think the fans could have stalled as the laptop works without a problem in windows XP even when the CPU usage is at around 100%.
please help.this problem is driving me crazy....

---

