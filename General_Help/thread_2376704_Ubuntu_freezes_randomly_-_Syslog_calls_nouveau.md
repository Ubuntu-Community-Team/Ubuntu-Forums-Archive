---
title: "Ubuntu freezes randomly - Syslog calls nouveau"
date: 2017-11-05
forum: General Help
---

### Post by kleinmuffin on 2017-11-05
Hey,

I recently installed Ubuntu, so I'm very new to Linux. Unfortunately Ubuntu will randomly stop working. The sound from Spotify, videos or other programs will continue while the whole screen freezes. If this happens I can't control anything anymore with my mouse or my keyboard. The only thing I can do then is to use REISUB trick to restart my pc.

I checked the syslog already but since I'm very new to Linux and Ubuntu I don't know what to do with this. In the following are the last lines after the freeze happens. Ubuntu freezed a few times now and the information in the syslog is very similar to the log I pasted here every time. 

```

Nov  5 12:46:14 patricePC kernel: [ 4735.348841] nouveau 0000:01:00.0: gr: TRAP ch 3 [005f884000 Xwayland[1571]]
Nov  5 12:46:14 patricePC kernel: [ 4735.348855] nouveau 0000:01:00.0: gr: GPC2/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp 90001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348864] nouveau 0000:01:00.0: gr: GPC3/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp c0001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348875] nouveau 0000:01:00.0: gr: TRAP ch 3 [005f884000 Xwayland[1571]]
Nov  5 12:46:14 patricePC kernel: [ 4735.348883] nouveau 0000:01:00.0: gr: GPC2/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp 140001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348891] nouveau 0000:01:00.0: gr: GPC3/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp d0001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348901] nouveau 0000:01:00.0: fifo: read fault at 000634e000 engine 00 [GR] client 0f [GPC1/PROP_0] reason 02 [PTE] on channel 3 [005f884000 Xwayland[1571]]
Nov  5 12:46:14 patricePC kernel: [ 4735.348908] nouveau 0000:01:00.0: fifo: channel 3: killed
Nov  5 12:46:14 patricePC kernel: [ 4735.348909] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Nov  5 12:46:14 patricePC kernel: [ 4735.348913] nouveau 0000:01:00.0: fifo: engine 0: scheduled for recovery
Nov  5 12:46:14 patricePC kernel: [ 4735.348924] nouveau 0000:01:00.0: gr: TRAP ch 3 [005f884000 Xwayland[1571]]
Nov  5 12:46:14 patricePC kernel: [ 4735.348931] nouveau 0000:01:00.0: gr: GPC2/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp c0001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348940] nouveau 0000:01:00.0: gr: GPC3/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp 0001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348954] nouveau 0000:01:00.0: gr: TRAP ch 3 [005f884000 Xwayland[1571]]
Nov  5 12:46:14 patricePC kernel: [ 4735.348964] nouveau 0000:01:00.0: gr: GPC2/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp 140001 [STACK_ERROR]
Nov  5 12:46:14 patricePC kernel: [ 4735.348975] nouveau 0000:01:00.0: gr: GPC3/TPC0/MP trap: global 00000004 [MULTIPLE_WARP_ERRORS] warp 30001 [STACK_ERROR]
Nov  5 12:46:14 patriNov  5 12:47:29 patricePC rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="802" x-info="http://www.rsyslog.com"] start
```

---

### Post by gauss4563 on 2017-11-05
Do you use Nouveau (nvidia GPU) + GNOME 3.26 + Wayland?
If so, then it's a known bug and I didn't find any solution but changing environment (from GNOME 3.26 to LXDE, for example)

---

### Post by kleinmuffin on 2017-11-05
I just use the vanilla installation of Ubuntu 17.10. I have a nvidia GPU, Gnome 3.26.1 and it seems like Ubuntu 17.10 uses Wayland.
How is it possible to change the environment and what would change for me? o:

---

### Post by gauss4563 on 2017-11-05
This should help you install:

[https://www.youtube.com/watch?v=9w8hkHSXu7w](https://www.youtube.com/watch?v=9w8hkHSXu7w)

---

### Post by kleinmuffin on 2017-11-05
Could I also install other drivers for the nvidia gpu to fix this issue?

---

### Post by gauss4563 on 2017-11-06
You could try, but in my case it did more harm than good and wrecked many things.

Another, more elegant work around which I've found and seems to work is to change the display manager from gdm3, which uses Wayland, to lightdm.

Just type: ```
[COLOR=#111111][FONT=Consolas]sudo apt-get install lightdm[/FONT][/COLOR]
```
and then choose lightdm. (The system will ask you to choose)

Or even simpler - just log in with Xorg instead of Wayland (gdm3 already has this option available)

---

### Post by kleinmuffin on 2017-11-07
Since I installed the Nvidia driver the problem doesn't appeared again, but if it do so, I will try this out. Thanks for you help :)

---

