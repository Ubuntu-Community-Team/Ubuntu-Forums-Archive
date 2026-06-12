---
title: "Performance lag every second or so"
date: 2020-06-08
forum: General Help
---

### Post by dex441 on 2020-06-08
Hello, long time on-off Ubuntu user here.

I've just installed Ubuntu 20.04 and updated it. I experience performance lag every second or so. It's like every second the processor is crippled and then it continues. It happens in games and it happens on the desktop, everywhere with anything. I've noticed that after boot-up there may be a few minutes where the lag doesn't happen, but not necessarily. I experience no such problem using Windows 10 or Debian. I'm using proprietary Nvidia Drivers.

---

### Post by HermanAB on 2020-06-08
To measure, is to know:
$ sudo top

---

### Post by dex441 on 2020-06-08
I don't really have to measure it, because it's obvious when I look at the screen.

---

### Post by HermanAB on 2020-06-08
If you don't really want to know why, or fix it, then why are you here?

---

### Post by dex441 on 2020-06-08
I understood it that you said I could only really know if it lagged if I could measure it. Obviously that's not true. But I just don't see how merely looking at the output of *top* has any use either. How would you diagnose the problem just looking at what *top* shows? It doesn't update rapidly enough. But nevertheless I can't see any pattern to the problem in *top*.

With that said, I've recorded CPU usage for a few minutes with *uptime*:

```
while true; do uptime >> uptime.log; sleep 0.01; done
```
[IMG]https://i.imgur.com/akQD84R.png[/IMG]

---

### Post by Autodave on 2020-06-08
You should be using the nVidia drivers from the repositories: never from the nVidia site.

---

### Post by dex441 on 2020-06-08
I just installed Ubuntu and didn't get the drivers from the Nvidia site. I recall that it's new in Ubuntu 20.04 that proprietary Nvidia drivers are included?

---

### Post by QIII on 2020-06-08
> **dex441 said:**
> I understood it that you said I could only really know if it lagged if I could measure it. Obviously that's not true. 

The problem is that without information, we cannot help you solve what you are experiencing.  Neither can you.  

What would you expect your doctor to say if you asked:  "Doctor, my knee hurts.  What's wrong?"  Could you reasonably expect them to tell you immediately?

---

### Post by TheFu on 2020-06-08
There are some common things that cause a system to seem slow.  Running **top** will show 4 of those quickly.
What's using all the CPU?  How many CPUs are there?
What's using all the RAM? How much RAM is there?
What's using all the network and disk I/O?

That's why HermanAB asked about top.
Unlabeled graphs aren't useful. 

We are volunteers. Helping us to help you seems obvious. Good luck with a solution.

---

### Post by dex441 on 2020-06-08
I wholly understand that it's not much to go on. But there's only really that much I can say. I experience periodic lag/stutter ever second or so, and it's only on Ubuntu 20.04.

---

### Post by dex441 on 2020-06-08
> **TheFu said:**
> There are some common things that cause a system to seem slow.  Running **top** will show 4 of those quickly.
What's using all the CPU?  How many CPUs are there?
What's using all the RAM? How much RAM is there?
What's using all the network and disk I/O?

That's why HermanAB asked about top.
Unlabeled graphs aren't useful. 

We are volunteers. Helping us to help you seems obvious. Good luck with a solution.

It's not slow per se. Games and stuff run fine, except the lag/stutter every second or so. And as I said, nothing in *top* says anything valuable. I made the graph showing the measured input from *uptime*, which might show systematic decrease in CPU usage over time, because the measurement is fine-grained enough. But it doesn't.

I assume it either is/or could become a problem for others too.

---

### Post by TheFu on 2020-06-08
Any errors or warnings in any system logs?  Failing storage or a failing cable can case re-sends due to CRC errors.
snaps?
kernel swappiness settings?
vm use?

---

### Post by dex441 on 2020-06-08
> **QIII said:**
> What would you expect your doctor to say if you asked:  "Doctor, my knee hurts.  What's wrong?"  Could you reasonably expect them to tell you immediately?

Not that it's really about this, but it's actually more like "So you're saying your knee hurts, but I can't measure your pain, so are you sure you really are in pain?".

Again, maybe I misunderstood grossly. I apologize if that's the case. I appreciate the help I can get. Let's not let this get out of hand. Again, I know it's not much to go on, but it's really just that much - intermittent lag/stutter ever second or so. I can't see anything relevant in *top* and I tried to provide some CPU logs that might be able to detect the lagging, which wasn't the case. It's just a standard Ubuntu 20.04 with an modern Nvidia GPU, and it's only under Ubuntu I have this problem.

---

### Post by dex441 on 2020-06-08
> **TheFu said:**
> Any errors or warnings in any system logs?  Failing storage or a failing cable can case re-sends due to CRC errors.
snaps?
kernel swappiness settings?
vm use?

No virtual machines in use, actually I've disabled it in BIOS. I highly doubt it has anything to do with networking, it happens both online and offline (even the cursor lags, everything lags). I don't know much about how system logs work in Ubuntu, sorry.

---

### Post by dex441 on 2020-06-08
What about this? This happens in /var/log/syslog and it keeps doing that (just a snippet). That can't be right?

```
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0):
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0):
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
Jun  8 22:10:20 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0):
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0):
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0):
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
Jun  8 22:10:21 Norwood /usr/lib/gdm3/gdm-x-session[1627]: (--) NVIDIA(GPU-0):
```

Similar stuff in /var/log/Xorg.0.log.

```
[    43.941] (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): connected
[    43.941] (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): Internal TMDS
[    43.941] (--) NVIDIA(GPU-0): Samsung S27E450 (DFP-0): 330.0 MHz maximum pixel clock
[    43.941] (--) NVIDIA(GPU-0):
[    43.941] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    43.941] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    43.941] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    43.941] (--) NVIDIA(GPU-0):
[    43.941] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    43.941] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    43.941] (--) NVIDIA(GPU-0): DFP-2: 2660.0 MHz maximum pixel clock
[    43.941] (--) NVIDIA(GPU-0):
[    43.941] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    43.942] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    43.942] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[    43.942] (--) NVIDIA(GPU-0):
[    43.942] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    43.942] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    43.942] (--) NVIDIA(GPU-0): DFP-4: 165.0 MHz maximum pixel clock
[    43.942] (--) NVIDIA(GPU-0):
[    56.511] (**) Option "fd" "40"
[    56.512] (II) event1  - Power Button: device removed
[    56.512] (**) Option "fd" "43"
[    56.513] (II) event0  - Power Button: device removed
[    56.513] (**) Option "fd" "44"
[    56.513] (**) Option "fd" "45"
[    56.513] (II) event2  - U: device removed
[    56.514] (**) Option "fd" "46"
[    56.514] (II) event4  - U Consumer Control: device removed
[    56.514] (**) Option "fd" "47"
[    56.514] (II) event6  - U System Control: device removed
[    56.515] (**) Option "fd" "44"
[    56.515] (II) event3  - Logitech M280/320/275: device removed
[    56.631] (II) systemd-logind: got pause for 13:64

```

---

### Post by TheFu on 2020-06-09
> **dex441 said:**
> No virtual machines in use, actually I've disabled it in BIOS. I highly doubt it has anything to do with networking, it happens both online and offline (even the cursor lags, everything lags). I don't know much about how system logs work in Ubuntu, sorry.

Sorry - in this case, "vm use" means "virtual memory".  vmstat.

My first 20.04 desktop install had terrible lagging. I'd selected to use ZFS (experimental). It was terrible, unusable, performance.  I did a fresh install NOT using ZFS and everything is fast.  Though it is a desktop and runs desktop applications, I mainly use it to run those applications from other systems, remotely.  The programs tend to be snaps and there are just many snaps that don't work on my normal systems (which isn't supposed to be a problem).

Logs on all Unix-like systems work the same way.  They are in /var/log/ ... there might be a GUI Log Viewer in your version. Use that to search for errors and warnings.  I'd use **egrep -i 'warn|errro' /var/log/*g**

---

### Post by dex441 on 2020-06-09
Thank you all for your help, but I've figured out the problem now. It turns out my DVI connector was loose. I must have pushed my computer when beginning to install Ubuntu.

Never in my life have I ever tried that a DVI-connector be connected well enough to never show any artifacts on the screen, or not make the screen go blank momentarily, yet be loose enough to cause what looked like performance lag. Truly baffling!

Again, thanks to everyone for your time.

---

