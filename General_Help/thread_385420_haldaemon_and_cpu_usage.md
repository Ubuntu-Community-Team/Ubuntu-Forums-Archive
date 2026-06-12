---
title: "haldaemon and cpu usage"
date: 2007-03-15
forum: General Help
---

### Post by bogler on 2007-03-15
Hi

I am running a 2.6.18 kernel as an experiment recently (i686 architecture) and i notice when i boot my machine that haldaemon processes are taking up around 30% of my CPU! (3.0G!)

I have read what i can on hald and still can't make much progress apart from killing the processes? So please if you know could you answer the questions below?

What is haldaemon? Do i need it? and Why is it so resource intensive?

heres a top

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
11564 haldaemo  25   0  7232 5696 1644 R 40.5  0.6   0:09.76 hald                                                                                            
 8024 root      16   0 84616  61m  10m S 11.5  6.1   7:21.03 Xorg                                                                                            
18644 david     15   0 15908 9292 7028 S  4.5  0.9   0:51.91 metacity                                                                                        
 8972 david     15   0  141m  43m  17m S  3.3  4.3   4:53.16 btdownloadgui

and heres a ps -aef117       6320     1  0 19:14 ?        00:00:00 /usr/lib/hal/hald-addon-storage
117      11564     1 33 21:39 ?        00:00:24 hald start
root     11565 11564  0 21:39 ?        00:00:00 hald-runner
117      11628 11565  0 21:39 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
117      11639 11565  0 21:39 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
117      11747 11565  0 21:39 ?        00:00:00 /usr/lib/hal/hald-addon-storage


CHEERS :guitar:

---

### Post by bogler on 2007-03-20
BUMP 

Someone must know something about haldaemon?

---

### Post by bogler on 2007-04-26
surely someone knows what hald is? and why i need it?

this process is eating up 30% of my cpu!

---

### Post by heldal on 2007-05-02
What's your hardware?

In particular note that the HAL daemon (hald) has problems with its handling of IDE devices (not SATA) on certain computers where harddrives and removable media share the same IDE-channel. In these cases you'll see the CPU spending quite some time in IO-wait (check top) and experience extremely slow loading of applications (unless cached). See ex in this tread: [http://ubuntuforums.org/showthread.php?t=188901]("http://ubuntuforums.org/showthread.php?t=188901")

---

