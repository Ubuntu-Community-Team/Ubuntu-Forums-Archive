---
title: "Ubuntu 16.04 wifi using a lot of battery"
date: 2017-09-19
forum: General Help
---

### Post by jonathan90 on 2017-09-19
I'm running 16.04 and my wifi seems to be using a ton of battery. Is this normal? Wifi was using 4.8 W while everything else was in the milliWatts.

```
PowerTOP 2.8      Overview   Idle stats   Frequency stats   Device stats   Tunables                                     

The battery reports a discharge rate of 16.2 W
The estimated remaining time is 1 hours, 52 minutes


Summary: 748.9 wakeups/second,  131.9 GPU ops/seconds, 0.0 VFS ops/sec and 45.6% CPU use


Power est.              Usage       Events/s    Category       Description
  4.80 W     35.1 pkts/s                Device         Network interface: wlp4s0 (iwlwifi)
 23.9 mW      1.5 ms/s      45.1        Process        /opt/google/chrome/chrome --type=gpu-process --field-trial-handle=453346121
 13.2 mW      8.3 ms/s      22.7        Process        compiz
 9.78 mW    358.0 ms/s      69.5        Process        /usr/lib/x86_64-linux-gnu/fwupd/fwupd
 4.79 mW     17.8 ms/s      22.3        Process        /opt/google/chrome/chrome
 599 µW      48.0 µs/s      0.10        Process        /usr/bin/xflux -z 14853 -k 4200 -nofork
    0 mW     16.8 µs/s      0.15        Process        /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
    0 mW     82.4 µs/s      0.25        Process        /usr/lib/gnome-terminal/gnome-terminal-server
    0 mW      8.7 µs/s      0.00        Process        gedit
    0 mW     17.5 ms/s      88.9        kWork          intel_mmio_flip_work_func
    0 mW     10.8 ms/s     106.6        Interrupt      [7] sched(softirq)
    0 mW      9.0 ms/s      13.2        Interrupt      [0] HI_SOFTIRQ
    0 mW      8.2 ms/s       6.9        Process        /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nol
    0 mW      6.1 ms/s       3.3        Process        /opt/google/chrome/chrome --type=renderer --field-trial-handle=453346121938
    0 mW      3.8 ms/s       2.2        Process        /home/jtong/Todoist/Todoist --type=zygote --no-sandbox
    0 mW      3.4 ms/s      70.0        Interrupt      PS/2 Touchpad / Keyboard / Mouse
    0 mW      2.4 ms/s     177.4        Timer          tick_sched_timer
    0 mW      0.9 ms/s     116.4        Timer          hrtimer_wakeup
    0 mW      0.8 ms/s       4.3        Interrupt      [126] i915
    0 mW    684.5 µs/s       0.6        kWork          delayed_fput
    0 mW    671.2 µs/s      18.8        Interrupt      [6] tasklet(softirq)
    0 mW    640.3 µs/s       1.0        Process        /opt/google/chrome/chrome --type=renderer --field-trial-handle=453346121938
    0 mW    541.7 µs/s      0.00        Interrupt      [1] timer(softirq)
    0 mW    461.5 µs/s      0.20        Process        /opt/google/chrome/chrome --type=renderer --field-trial-handle=453346121938
    0 mW    430.8 µs/s      0.00        Interrupt      [9] RCU(softirq)
    0 mW    341.4 µs/s       5.2        Interrupt      [20] intel_ish_ipc
    0 mW    312.4 µs/s      0.20        Process        /opt/google/chrome/chrome --type=renderer --field-trial-handle=453346121938
    0 mW    284.1 µs/s      0.05        Process        [kworker/u8:22]
    0 mW    283.2 µs/s      11.8        kWork          intel_unpin_work_fn
    0 mW    233.1 µs/s      0.00        Timer          process_timeout

```

---

### Post by Autodave on 2017-09-19
I have no idea. However, remember that your wifi is a transmitter as well as a receiver. Receiving takes very little power, transmitting takes many times more. It really doesn't seem excessive to me.

Are you concerned about battery life? If you don't need the wifi at any particular time, you could always shut the wifi off to conserve power..........

---

